---
title: "カスタム アセンブリの配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- deploying custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], deploying
- custom assemblies [Reporting Services], updating
- updating custom assemblies
ms.assetid: c6674cd8-0de7-4a5a-9e7c-12ffa49f6fd2
caps.latest.revision: 46
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: bae986bea4e252d15bce495892e60c2a7e7d6064
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="deploying-a-custom-assembly"></a>カスタム アセンブリの配置
  カスタム アセンブリを展開する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、レポート デザイナーとレポート サーバーの両方のアプリケーション フォルダーにアセンブリを配置します。 既定では、カスタム アセンブリが与えられます**実行**でアクセス許可[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。 カスタム アセンブリを許可する Execute 権限よりも高い権限を必要があります、レポート サーバーの rssrvpolicy.config 構成ファイルおよびレポート デザイナー プレビュー ウィンドウの rspreviewpolicy.config 構成ファイルを編集します。 または、グローバル アセンブリ キャッシュ (GAC) にカスタム アセンブリをインストールできます。  
  
> [!NOTE]  
>  レポート デザイナー プレビュー 2 つのモードがある: [プレビュー] タブと、レポート プロジェクトを開始したときに起動されるポップアップ プレビュー ウィンドウ**DebugLocal**モード。 [プレビュー] タブを使用してすべてのレポート式の実行、 **FullTrust**アクセス許可が設定され、セキュリティ ポリシー設定は適用されません。 レポート サーバー機能のシミュレーションを目的としているプレビュー ウィンドウには、ポリシー構成ファイルが備わっています。レポート デザイナーでカスタム アセンブリを使用する場合、ユーザーまたは管理者はこの構成ファイルを変更する必要があります。 また、このポップアップ プレビュー ウィンドウでは、カスタム アセンブリがロックされます。 したがって、カスタム アセンブリ コードを変更または更新するには、プレビュー ウィンドウを閉じる必要があります。  
  
###### <a name="to-deploy-a-custom-assembly-in-reporting-services"></a>カスタム アセンブリを Reporting Services に配置するには  
  
1.  カスタム アセンブリを構築場所からレポート サーバーの bin フォルダーまたはレポート デザイナーのフォルダーにコピーします。 レポート サーバーの bin フォルダーの既定の場所は、%ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin です。 レポート デザイナー フォルダーの既定の場所は、%ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies です。  
  
     カスタム アセンブリをレポート サーバーの bin フォルダーに配置した場合は、このカスタム アセンブリを参照するレポートをパブリッシュできます。レポート デザイナー フォルダーに配置した場合は、このカスタム アセンブリを参照するレポートをレポート デザイナーで実行およびデバッグできます。  
  
     カスタム アセンブリ コードに既定の実行権限よりも上位の権限を付与するには、次の操作を行います。  
  
2.  適切な構成ファイルを開きます。 rssrvpolicy.config の既定の場所は、%ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer です。 rspreviewpolicy.config の既定の場所は、%ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies です。  
  
3.  カスタム アセンブリのコード グループを追加します。 詳細については、次を参照してください。[セキュリティで保護された開発 & #40 です。Reporting Services &#41;](../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="updating-custom-assemblies"></a>カスタム アセンブリの更新  
 ある時点では、パブリッシュされた複数のレポートが参照するカスタム アセンブリのバージョンの更新が必要なことがあります。 このようなアセンブリがレポート サーバーまたはレポート デザイナーの bin ディレクトリに既に存在し、アセンブリのバージョン番号が何らかの方法で増加するか変わった場合は、現在パブリッシュされているレポートが適切に機能しなくなります。 参照されるアセンブリのバージョンを更新する必要があります、 **CodeModules**レポート定義の要素およびレポートを再パブリッシュします。 カスタム アセンブリを頻繁に更新することがあらかじめわかっていて、現在パブリッシュされているレポートが新しいアセンブリを参照する必要がある場合は、特定のアセンブリのすべての更新に同じバージョン番号を使用することを検討してください。  
  
 現在パブリッシュされているレポートがアセンブリの新バージョンを参照する必要がない場合は、カスタム アセンブリをグローバル アセンブリ キャッシュに配置できます。 グローバル アセンブリ キャッシュは同じアセンブリのバージョンを複数保持できるため、現在のレポートがアセンブリの旧バージョンを参照し、新しくパブリッシュされたレポートが更新されたアセンブリを参照できます。 別の方法として、レポート サーバーのリダイレクトのバインドを設定し、旧アセンブリの全要求を新しいアセンブリに強制的にリダイレクトすることもできます。 レポート サーバーの Web.config ファイルとレポート サーバーの ReportService.exe.config ファイルを変更する必要があります。 エントリは、次のようになります。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 [レポートでのカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [アセンブリとグローバル アセンブリ キャッシュ](http://go.microsoft.com/fwlink/?LinkId=63912)  
  
  