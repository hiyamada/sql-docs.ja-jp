---
title: カスタム接続マネージャーのコーディング | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], coding
ms.assetid: b12b6778-1f01-4a7d-984d-73f2f7630aa5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d2c4c428f3d18c914f1515dbb638b50e11150d38
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190892"
---
# <a name="coding-a-custom-connection-manager"></a>カスタム接続マネージャーのコーディング
  <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基本クラスを継承するクラスを作成し、<xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 属性をそのクラスに適用したら、基本クラスのプロパティとメソッドの実装をオーバーライドして、カスタム機能を提供する必要があります。  
  
 カスタム接続マネージャーのサンプルについては、「[カスタム接続マネージャー用ユーザー インターフェイスの開発](developing-a-user-interface-for-a-custom-connection-manager.md)」を参照してください。 このトピック内のコード例は、SQL Server カスタム接続マネージャーのサンプルに含まれています。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に組み込まれているタスク、変換元、および変換先の多くは、組み込みの接続マネージャーの特定の種類でのみ機能します。 そのため、これらのサンプルは組み込みのタスクおよびコンポーネントではテストできません。  
  
## <a name="configuring-the-connection-manager"></a>接続マネージャーの構成  
  
### <a name="setting-the-connectionstring-property"></a>ConnectionString プロパティの設定  
 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> プロパティは重要なプロパティです。このプロパティだけが、カスタム接続マネージャーごとに一意です。 接続マネージャーは、このプロパティの値を使用して、外部のデータ ソースへ接続します。 サーバー名やデータベース名など、他の複数のプロパティを組み合わせて接続文字列を作成する場合は、接続文字列テンプレートの一部の値をユーザー指定による新しい値に置き換えることによって文字列をアセンブルするためのヘルパー関数を使用できます。 次のコード例は、ヘルパー関数を使用して文字列をアセンブルする <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> プロパティを実装する方法を示しています。  
  
```vb  
' Default values.  
Private _serverName As String = "(local)"  
Private _databaseName As String = "AdventureWorks"  
Private _connectionString As String = String.Empty  
  
Private Const CONNECTIONSTRING_TEMPLATE As String = _  
  "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI"  
  
Public Property ServerName() As String  
  Get  
    Return _serverName  
  End Get  
  Set(ByVal value As String)  
    _serverName = value  
  End Set  
End Property  
  
Public Property DatabaseName() As String  
  Get  
    Return _databaseName  
  End Get  
  Set(ByVal value As String)  
    _databaseName = value  
  End Set  
End Property  
  
Public Overrides Property ConnectionString() As String  
  Get  
    UpdateConnectionString()  
    Return _connectionString  
  End Get  
  Set(ByVal value As String)  
    _connectionString = value  
  End Set  
End Property  
  
Private Sub UpdateConnectionString()  
  
  Dim temporaryString As String = CONNECTIONSTRING_TEMPLATE  
  
  If Not String.IsNullOrEmpty(_serverName) Then  
    temporaryString = temporaryString.Replace("<servername>", _serverName)  
  End If  
  If Not String.IsNullOrEmpty(_databaseName) Then  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName)  
  End If  
  
  _connectionString = temporaryString  
  
End Sub  
```  
  
```csharp  
// Default values.  
private string _serverName = "(local)";  
private string _databaseName = "AdventureWorks";  
private string _connectionString = String.Empty;  
  
private const string CONNECTIONSTRING_TEMPLATE = "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI";  
  
public string ServerName  
{  
  get  
  {  
    return _serverName;  
  }  
  set  
  {  
    _serverName = value;  
  }  
}  
  
public string DatabaseName  
{  
  get  
  {  
    return _databaseName;  
  }  
  set  
  {  
    _databaseName = value;  
  }  
}  
  
public override string ConnectionString  
{  
  get  
  {  
    UpdateConnectionString();  
    return _connectionString;  
  }  
  set  
  {  
    _connectionString = value;  
  }  
}  
  
private void UpdateConnectionString()  
{  
  
  string temporaryString = CONNECTIONSTRING_TEMPLATE;  
  
  if (!String.IsNullOrEmpty(_serverName))  
  {  
    temporaryString = temporaryString.Replace("<servername>", _serverName);  
  }  
  
  if (!String.IsNullOrEmpty(_databaseName))  
  {  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName);  
  }  
  
  _connectionString = temporaryString;  
  
}  
```  
  
### <a name="validating-the-connection-manager"></a>接続マネージャーの検証  
 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> メソッドをオーバーライドして、接続マネージャーが正しく構成されていることを確認します。 少なくとも、接続文字列の形式を検証し、すべての引数に値が指定されていることを確認してください。 接続マネージャーが <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> メソッドから <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> を返すまでは、実行を続行できません。  
  
 次のコード例は、接続用のサーバー名がユーザーによって指定されていることを確認する <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> の実装を示します。  
  
```vb  
Public Overrides Function Validate(ByVal infoEvents As Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents) As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  If String.IsNullOrEmpty(_serverName) Then  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0)  
    Return DTSExecResult.Failure  
  Else  
    Return DTSExecResult.Success  
  End If  
  
End Function  
```  
  
```csharp  
public override Microsoft.SqlServer.Dts.Runtime.DTSExecResult Validate(Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents infoEvents)  
{  
  
  if (String.IsNullOrEmpty(_serverName))  
  {  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0);  
    return DTSExecResult.Failure;  
  }  
  else  
  {  
    return DTSExecResult.Success;  
  }  
  
}  
```  
  
### <a name="persisting-the-connection-manager"></a>接続マネージャーの保存  
 通常、接続マネージャーに対して、カスタムの永続性を実装する必要はありません。 カスタムの永続性は、オブジェクトのプロパティで複合データ型が使用されている場合にのみ必要です。 詳細については、「[Integration Services 用のカスタム オブジェクトの開発](../developing-custom-objects-for-integration-services.md)」を参照してください。  
  
## <a name="working-with-the-external-data-source"></a>外部データ ソースの使用  
 外部データ ソースへの接続をサポートするメソッドは、カスタム接続マネージャーにとって非常に重要なメソッドです。 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> メソッドおよび <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> メソッドは、デザイン時と実行時のさまざまな時点で呼び出されます。  
  
### <a name="acquiring-the-connection"></a>接続の取得  
 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> メソッドの使用時にカスタム接続マネージャーが返すオブジェクトについて、適切な種類を決定する必要があります。 たとえば、ファイル接続マネージャーは、パスとファイル名が含まれた文字列のみを返し、ADO.NET 接続マネージャーは、既に開いているマネージド接続オブジェクトを返します。 OLE DB 接続マネージャーは、マネージド コードから使用できないネイティブの OLE DB 接続オブジェクトを返します。 このトピック内のコード スニペットの基になっているカスタム SQL Server 接続マネージャーは、開いている `SqlConnection` オブジェクトを返します。  
  
 接続マネージャーのユーザーは、返されるオブジェクトを適切な種類にキャストし、そのメソッドとプロパティにアクセスできるよう、オブジェクトの種類をあらかじめ知っておく必要があります。  
  
```vb  
Public Overrides Function AcquireConnection(ByVal txn As Object) As Object  
  
  Dim sqlConnection As New SqlConnection  
  
  UpdateConnectionString()  
  
  With sqlConnection  
    .ConnectionString = _connectionString  
    .Open()  
  End With  
  
  Return sqlConnection  
  
End Function  
```  
  
```csharp  
public override object AcquireConnection(object txn)  
{  
  
  SqlConnection sqlConnection = new SqlConnection();  
  
  UpdateConnectionString();  
  
  {  
    sqlConnection.ConnectionString = _connectionString;  
    sqlConnection.Open();  
  }  
  
  return sqlConnection;  
  
}  
```  
  
### <a name="releasing-the-connection"></a>接続の解放  
 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> メソッドでのアクションは、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> メソッドから返されたオブジェクトの種類によって異なります。 開いている接続オブジェクトがあれば、それを閉じて、使用中のリソースを解放してください。 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> から文字列値のみが返された場合、必要なアクションはありません。  
  
```vb  
Public Overrides Sub ReleaseConnection(ByVal connection As Object)  
  
  Dim sqlConnection As SqlConnection  
  
  sqlConnection = DirectCast(connection, SqlConnection)  
  
  If sqlConnection.State <> ConnectionState.Closed Then  
    sqlConnection.Close()  
  End If  
  
End Sub  
```  
  
```csharp  
public override void ReleaseConnection(object connection)  
{  
  SqlConnection sqlConnection;  
  sqlConnection = (SqlConnection)connection;  
  if (sqlConnection.State != ConnectionState.Closed)  
    sqlConnection.Close();  
}  
```  
  
![Integration Services のアイコン (小)](../../media/dts-16.gif "Integration Services アイコン (小)")**Integration Services の日付を維持します。** <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照してください。](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>参照  
 [カスタム接続マネージャーの作成](creating-a-custom-connection-manager.md)   
 [カスタム接続マネージャー用ユーザー インターフェイスの開発](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
