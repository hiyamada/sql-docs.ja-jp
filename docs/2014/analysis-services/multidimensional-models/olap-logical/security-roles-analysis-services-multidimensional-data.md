---
title: セキュリティ ロール (Analysis Services - 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], roles
- Analysis Services objects, roles
- security [Analysis Services], roles
- roles [Analysis Services], about roles
- server roles [Analysis Services]
- database roles [Analysis Services]
- roles [Analysis Services]
- storing data [Analysis Services], roles
- access rights [Analysis Services], roles
ms.assetid: 5b7e9cef-ff68-4d8e-99bc-e0094ced1baa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4400755b5a117b16f56fe191cf0e2c80da03261c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164652"
---
# <a name="security-roles--analysis-services---multidimensional-data"></a>セキュリティ ロール (Analysis Services - 多次元データ)
  ロールで使用[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のセキュリティを管理する[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]オブジェクトおよびデータ。 基本的な用語では、ロールは Microsoft Windows ユーザーと特定のアクセス権とアクセス許可のインスタンスによって管理されるオブジェクトの定義を持つグループのセキュリティ識別子 (Sid) を関連付けます。[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。 2 種類のロールが記載[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:  
  
-   サーバー ロール。管理者が [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスにアクセスできるようにするための固定ロールです。  
  
-   データベース ロール。管理者以外のユーザーによるオブジェクトやデータへのアクセスを制御するために、管理者によって定義されるロールです。  
  
 セキュリティの[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]セキュリティは、ロールとアクセス許可を使用して管理します。 ロールはユーザーのグループです。 ユーザー (メンバーとも呼ばれる) はロールに追加したり、ロールから削除したりできます。 オブジェクトに対する権限はロールによって指定されます。ロールのすべてのメンバーは、そのロールが権限を持つオブジェクトを使用できます。 ロールのすべてのメンバーは、オブジェクトに対して等しい権限を持ちます。 権限はオブジェクトに対して適用されます。 各オブジェクトは、そのオブジェクトに対して許可された権限のコレクションを持ちます。複数の異なる権限セットを 1 つのオブジェクトに付与できます。 オブジェクトの権限コレクションに含まれる各権限には、1 つのロールが割り当てられています。  
  
## <a name="role-and-role-member-objects"></a>Role オブジェクトと Role Member オブジェクト  
 ロールは、ユーザー (メンバー) のコレクションを格納するオブジェクトです。 ロールの定義内のユーザーのメンバーシップを確立する[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。 権限はロールに基づいて割り当てられます。したがって、ユーザーがオブジェクトにアクセスするためには、いずれかのロールのメンバーになる必要があります。  
  
 <xref:Microsoft.AnalysisServices.Role> オブジェクトは、Name、ID、および Members の各パラメーターで構成されます。 Members は文字列のコレクションです。 各メンバーには "domain\username" という形式のユーザー名が含まれます。 Name はロールの名前を表す文字列です。 ID はロールの一意な識別子を表す文字列です。  
  
### <a name="server-role"></a>サーバー ロール  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]サーバー ロールのインスタンスに Windows ユーザーとグループの管理アクセス権を定義する[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。 このロールのメンバーがすべてにアクセス権を持つ[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベースおよびインスタンス上のオブジェクト[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、し、次のタスクを実行できます。  
  
-   SQL Server Management Studio または [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] を使用して、データベースの作成やサーバーレベルのプロパティの設定など、サーバーレベルの管理機能を実行する。  
  
-   分析管理オブジェクト (AMO) を使用して、プログラムで管理機能を実行する。  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のデータベース ロールを保守する。  
  
-   トレースを開始する (プロセス アクセス権を持つデータベース ロールによって実行可能な処理イベントを除く)。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の各インスタンスには、そのインスタンスを管理できるユーザーを定義するサーバー ロールがあります。 このロールの名前と ID は Administrators で、データベース ロールとは異なり、サーバー ロールは削除できず、権限を追加または削除することもできません。 つまり、ユーザーがまたはのいずれかのインスタンスの管理者ではない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]自分がそのインスタンスのサーバーの役割に含まれるかどうかに応じて、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
### <a name="database-roles"></a>データベース ロール  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース ロール オブジェクトとデータに対するユーザー アクセスを定義する、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。 データベース ロールは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース内に個別のオブジェクトとして作成され、そのロールが作成されたデータベースのみに適用されます。 Windows ユーザーおよびグループは、管理者によってこのロールに含まれています。管理者は、このロール内の権限も定義します。  
  
 ロールの権限は、メンバーがデータベース内のオブジェクトとデータだけでなく、データベース自体にアクセスして管理できるようにするものです。 各権限には 1 つまたは複数のアクセス権が関連付けられており、アクセス権によってデータベース内の特定のオブジェクトへのアクセスをさらに詳細に制御できるようになっています。  
  
## <a name="permission-objects"></a>Permission オブジェクト  
 権限は、各ロールについて、オブジェクト (キューブやディメンションなど) に関連付けられます。 権限は、ロールのメンバーがオブジェクトに対して実行できる操作を指定します。  
  
 <xref:Microsoft.AnalysisServices.Permission> クラスは抽象クラスです。 そのため、対応するオブジェクトに権限を定義するには、派生クラスを使用する必要があります。 オブジェクトごとに権限の派生クラスが定義されます。  
  
|オブジェクト|クラス|  
|------------|-----------|  
|<xref:Microsoft.AnalysisServices.Database>|<xref:Microsoft.AnalysisServices.DatabasePermission>|  
|<xref:Microsoft.AnalysisServices.DataSource>|<xref:Microsoft.AnalysisServices.DataSourcePermission>|  
|<xref:Microsoft.AnalysisServices.Dimension>|<xref:Microsoft.AnalysisServices.DimensionPermission>|  
|<xref:Microsoft.AnalysisServices.Cube>|<xref:Microsoft.AnalysisServices.CubePermission>|  
|<xref:Microsoft.AnalysisServices.MiningStructure>|<xref:Microsoft.AnalysisServices.MiningStructurePermission>|  
|<xref:Microsoft.AnalysisServices.MiningModel>|<xref:Microsoft.AnalysisServices.MiningModelPermission>|  
  
 権限によって使用可能となるアクションを以下の一覧に示します。  
  
|操作|値|説明|  
|------------|------------|-----------------|  
|Process|{`true`, `false`}<br /><br /> 既定値 = `false`|`true` を指定した場合、メンバーはこのオブジェクトと、このオブジェクトに含まれる任意のオブジェクトを処理できます。<br /><br /> Process 権限はマイニング モデルには適用されません。 <xref:Microsoft.AnalysisServices.MiningModel> アクセス許可が常に継承<xref:Microsoft.AnalysisServices.MiningStructure>します。|  
|ReadDefinition|{`None`, `Basic`, `Allowed`}<br /><br /> 既定値 = `None`|オブジェクトに関連付けられたデータ定義 (ASSL) をメンバーが読み取れるかどうかを指定します。<br /><br /> `Allowed` を指定した場合、メンバーはオブジェクトに関連付けられた ASSL を読み取ることができます。<br /><br /> `Basic` `Allowed`オブジェクトに含まれるオブジェクトによって継承されます。 `Allowed` オーバーライド`Basic`と`None`します。<br /><br /> オブジェクトで DISCOVER_XML_METADATA を使用する場合、`Allowed` を指定する必要があります。 `Basic` リンクされたオブジェクトとローカル キューブを作成する必要です。|  
|Read|{`None`, `Allowed`}<br /><br /> 既定 =`None` (dimensionpermission の場合、既定値 =`Allowed`)|スキーマ行セットおよびデータ コンテンツへの読み取りアクセスがメンバーにあるかどうかを指定します。<br /><br /> `Allowed` データベースを検出できるデータベースの読み取りアクセス権がわかります。<br /><br /> キューブに対して `Allowed` を指定した場合は、<xref:Microsoft.AnalysisServices.CellPermission> および <xref:Microsoft.AnalysisServices.CubeDimensionPermission> による制限がない限り、スキーマ行セットおよびキューブ コンテンツへの読み取りアクセスが許可されます。<br /><br /> ディメンションに対して `Allowed` を指定した場合は、<xref:Microsoft.AnalysisServices.CubeDimensionPermission> による制限がない限り、ディメンション内のすべての属性への読み取り権限が許可されます。 Read (読み取り) 権限は、<xref:Microsoft.AnalysisServices.CubeDimensionPermission> の静的継承でのみ使用されます。 ディメンションに対して `None` を指定した場合は、ディメンションが非表示になり、集計可能な属性への既定のメンバーのアクセスのみが許可されます。ディメンションに集計不能な属性が含まれる場合はエラーが発生します。<br /><br /> <xref:Microsoft.AnalysisServices.MiningModelPermission> に対して `Allowed` を指定した場合は、スキーマ行セット内のオブジェクトの表示権限と、予測結合の実行権限が許可されます。<br /><br /> **NoteAllowed**するデータベース内のオブジェクトに対する読み取りまたは書き込みが必要です。|  
|Write|{`None`, `Allowed`}<br /><br /> 既定値 = `None`|親オブジェクトのデータへの書き込みアクセスがメンバーにあるかどうかを指定します。<br /><br /> <xref:Microsoft.AnalysisServices.Dimension>、<xref:Microsoft.AnalysisServices.Cube>、および <xref:Microsoft.AnalysisServices.MiningModel> の各サブクラスにアクセスが適用されます。 データベースには適用されません<xref:Microsoft.AnalysisServices.MiningStructure>サブクラスで、検証エラーが生成されます。<br /><br /> <xref:Microsoft.AnalysisServices.Dimension> に対して `Allowed` を指定した場合は、ディメンション内のすべての属性への書き込み権限が許可されます。<br /><br /> <xref:Microsoft.AnalysisServices.Cube> に対して `Allowed` を指定した場合は、Type=writeback として定義された各パーティションについて、キューブのセルへの書き込み権限が許可されます。<br /><br /> <xref:Microsoft.AnalysisServices.MiningModel> に対して `Allowed` を指定した場合は、モデル コンテンツの変更権限が許可されます。<br /><br /> `Allowed` <xref:Microsoft.AnalysisServices.MiningStructure>特定の意味を持たない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。 **注:** に書き込みを設定することはできません`Allowed`読み取りも設定しない限り、 `Allowed`|  
|管理**注:** では、データベースのアクセス許可のみ|{`true`, `false`}<br /><br /> 既定値 = `false`|メンバーがデータベースを管理できるかどうかを指定します。<br /><br /> `true` メンバー データベース内のすべてのオブジェクトへのアクセスを付与します。<br /><br /> メンバーは特定のデータベースに対してのみ管理権限を持つことができます。他のデータベースを管理することはできません。|  
  
## <a name="see-also"></a>参照  
 [オブジェクトと操作へのアクセスの承認&#40;Analysis Services&#41;](../authorizing-access-to-objects-and-operations-analysis-services.md)  
  
  
