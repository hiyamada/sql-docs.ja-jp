---
title: 正常性ルールのリファレンス (Power Pivot for SharePoint) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b3beb9b320044ce76ff7e6302e81041f44b600d5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="health-rules-reference-power-pivot-for-sharepoint"></a>正常性ルールのリファレンス (Power Pivot for SharePoint)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  ここでは、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint のインストールによって追加される SharePoint の正常性ルールについて説明します。 正常性ルールは、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] サービス アプリケーションまたはそれに関連する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー状態、可用性、または構成に関する問題をレポートするために使用されます。  
  
 次の表に示すルールは、SharePoint サーバーの全体管理の [正常性アナライザー ルールの定義] ページに表示される順に示されています。 構成可能なルールでは、ルールがトリガーされるしきい値を変更できます。 詳細については、「 [Power Pivot の正常性ルールの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md)」を参照してください。 "自動修復" は、問題のレポートのページからクリックして、問題を解決できる修復機能が組み込まれていることを示しています。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 **注:** [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] によってインストールされる正常性ルール セットは、SharePoint のバージョンに応じて異なります。 下記の表の "バージョン" 列を参照してください。または、次の Windows PowerShell コマンドを実行して、インストールされたルールを確認することもできます。  
  
```  
Get-SPHealthAnalysisRule | select name, enabled, summary | where {$_.summary -like “*power*”}  | format-table -property * -autosize | out-default  
```  
  
|Rule|構成可能|自動修復|バージョン|Description|  
|----------|------------------|-----------------|-------------|-----------------|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Analysis Services OLE DB プロバイダーはこのコンピューターにインストールされていません。|いいえ|いいえ|SharePoint 2010|Analysis Services OLE DB プロバイダーがサーバーにインストールされていないか、バージョンが正しくありません。 このルールは、SharePoint ファーム内の [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint がインストールされていないアプリケーション サーバー上に Excel Services のインスタンスが存在する場合に表示されます。 Excel Services が [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] データに接続するために使用する Analysis Services OLE DB プロバイダーがインストールされていないことを警告しています。 この問題を解決するには、Analysis Services OLE DB プロバイダーがインストールされていない各 Excel Services サーバーに OLE DB プロバイダーをインストールします。 Analysis Services OLE DB プロバイダーは、Microsoft ダウンロード センターからダウンロードしてインストールできます。 詳細については、「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: MSOLAP プロバイダーの SQL Server 2008 R2 バージョンをこのコンピューターにインストールしましたが、Microsoft.AnalysisServices.ChannelTransport.dll のレジストリ設定が有効な設定になっていません。|いいえ|はい|SharePoint 2010|これは、サーバー構成の問題です。 ほとんどの場合、ChannelTransport.dll がグローバル アセンブリに登録されていないことが原因です。 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint がインストールされている各サーバーに ChannelTransport.dll を登録するには、このルールの自動修復を実行します。 また、regasm.exe を手動で実行して、ファイルを登録することもできます。 SharePoint Timer Service がローカル管理者として実行されていない場合は、手動で登録する必要があります。 レジストリ設定の更新に失敗すると、Excel Services と [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] System サービス間のサーバー通信が低速になります。セキュリティ構成によっては、接続エラーが発生する場合があります。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションには、この操作を実行する権限が与えられていません。|いいえ|いいえ|SharePoint 2010|このルールでは、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの ID が [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サーバー アプリケーション データベースのデータベース所有者であり、ローカルの SQL Server Analysis Services インスタンスに対する管理権限を持っているかどうかを確認します。 これらの権限は、インストール中および配置中に自動的に付与されますが、この手順が正常に完了しなかった場合は、この正常性ルールがトリガーされます。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの ID をローカルの Administrators グループのメンバーにすることはできません。|いいえ|いいえ|SharePoint 2010|これは、配置全体のセキュリティを強化するベスト プラクティスです。 ローカルの管理者グループに属するアカウントで実行するように [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションを構成した場合は、サービス アカウントをそのグループに属していないアカウントに変更する必要があります。 各サービス専用の最小特権アカウントを使用することをお勧めします。 そうすることで、サービスが分離され、ログインの監査が簡単になります。 サービス アカウントの変更の詳細については、「 [Configure Power Pivot Service Accounts](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Analysis Services インスタンスは表形式モードで実行しますが、このモードを指定する構成設定がオフになっています。|いいえ|いいえ|SharePoint 2010|このルールでは、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint インストールの SQL Server Analysis Services インスタンスで **DeploymentMode** サーバー プロパティが 1 に設定されているかどうかを確認します。 このプロパティが別の値に設定されている場合、またはルール チェッカーを実行する SharePoint Timer Service にファイルを開く権限がない場合、このルールは失敗します。 配置モード プロパティの詳細については、「 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] データ更新タイマー ジョブが無効になっています。|いいえ|いいえ|SharePoint 2013<br /><br /> SharePoint 2010|タイマー ジョブが有効になっていることを確認するには、タイマー ジョブの設定を確認します。 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] のデータ更新機能を使用していない場合は、このルールを無視できます。 詳細については、「 [SharePoint 2010 での PowerPivot データ更新](http://msdn.microsoft.com/en-us/01b54e6f-66e5-485c-acaa-3f9aa53119c9)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: SQL Server 構成マネージャーで管理されている SQL Server Analysis Services ([!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]) サービス アカウント情報が、サーバー全体管理で管理されているアカウント情報と異なります。|いいえ|いいえ|SharePoint 2010|このルールでは、SQL Server 構成マネージャーのサービス アカウント情報が、同じ Analysis Services インスタンスのサーバーの全体管理における管理アカウント情報と同一かどうかを確認します。 アカウントが異なる場合は、SQL Server 構成マネージャーのサービス アカウント情報を変更して、サーバーの全体管理で指定されたアカウントに戻すことができるように、"問題と解決策" レポートにエンティティが追加されます。 SQL Server 構成マネージャーは、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint インストールのサービス アカウントのユーザー名またはパスワードを変更するためのツールとして使用できません。 サーバーの全体管理を使用すると、SharePoint の管理アカウント機能を使用できます。 さらに、ファームに [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint サーバーが複数ある場合、サービス アカウントの設定に一貫性がないと、サービス情報の正しくないサーバーの処理操作とクエリ操作が中断される可能性があります。<br /><br /> 1 つのサーバーでこのルールがトリガーされた場合、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックは一時的に機能しますが、問題をできるだけ早く解決することをお勧めします。 データベースとファイル システムの権限は、サーバーの全体管理で指定されたアカウント情報を使用して更新されます。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: 配置済みのファーム ソリューションが最新ではありません。|いいえ|はい|SharePoint 2010|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint のインストールでは、ファーム レベルのソリューションと Web アプリケーション レベルのソリューションを使用して、その機能をインストールします。 このルールは、ファーム ソリューションがバージョン、サーバー、または Web ソリューションに対して最新でないことを示します。 ほとんどの場合、これはサーバーの配置の問題です。 この問題を解決するには、SQL Server セットアップを実行して、ファーム内のいずれかの [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint のインストールを修復することを検討してください。 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint のインストールにおけるソリューションの詳細については、「 [SharePoint への PowerPivot ソリューションの配置](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: 全体的な CPU 使用率が高すぎます。|はい|いいえ|SharePoint 2010|このルールでは、システム レベルの CPU 消費量がレポートされます。 サーバーの状態に基づいてファーム内の複数の [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint サーバー間で負荷を分散する関係で、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] System サービスではサーバーの状態を示す尺度として CPU 使用率を使用するため、全体的な CPU 使用率が監視されます。 ファームに別のアプリケーション サーバーを追加し、CPU を集中的に使用するアプリケーションをそのサーバーに移動することを検討してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Analysis Services には要求された操作を実行するのに十分な CPU リソースがありません。|はい|いいえ|SharePoint 2010|Analysis Services プロセス (msmdsrv.exe) に使用できる CPU リソースの量が、このサーバーのアクティビティ レベルに対して不足しています。 ファームに別の [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint サーバーを追加することを検討してください。 詳細については、「 [配置のチェック リスト: SharePoint 2010 ファームへの PowerPivot サーバーの追加によるスケールアウト](http://msdn.microsoft.com/library/2dbddcc7-427a-4537-a8e2-56d99b9d967d)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Analysis Services には要求された操作を実行するのに十分なメモリがありません。|いいえ|いいえ|SharePoint 2010|このルールは、Analysis Services の使用可能なメモリが 5% しか残っていない場合にトリガーされます。 SharePoint アプリケーション サーバー上の SQL Server Analysis Services インスタンスには、常に未使用のメモリをいくらか確保しておく必要があります。 サーバーのほとんどの操作はメモリ バインドされているため、サーバーは上限まで実行されない場合に最適に実行されます。<br /><br /> 既定では、使用可能なメモリが 5% にまで下がると、メモリ不足の警告が発生します。 Analysis Services インスタンスの設定を調整して、この値を増減させることができます。 詳細については、「 [Power Pivot の正常性ルールの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md)」を参照してください。<br /><br /> 5% の未使用メモリは、Analysis Services に割り当てられているメモリに対する割合として計算されます。 たとえば、メモリの合計が 200 GB で、Analysis Services にその 80% (つまり 160 GB) が割り当てられている場合、5% の未使用メモリは 160 GB の 5% (つまり 8 GB) です。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: 大量の接続は、現在の負荷を処理するにはより多くのサーバーを配置する必要があることを示しています。|はい|いいえ|SharePoint 2010|既定では、この正常性ルールは、異なるユーザー接続の数が 100 を超えている場合にトリガーされます。 この既定値は恣意的なものです (サーバーのハードウェアの仕様やユーザーの利用状況に基づいていません)。そのため、使用している環境のサーバー容量およびユーザーの利用状況に応じて、値を増減できます。 詳細については、「 [Power Pivot の正常性ルールの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: 接続に対する読み込みイベントの比率が高すぎます。|はい|いいえ|SharePoint 2013<br /><br /> SharePoint 2010|既定では、この正常性ルールは、接続イベントに対する読み込みイベントの比率がデータ収集期間全体 (既定では 4 時間) の 50% を超えている場合にトリガーされます。 比率が高い場合は、一意のブックへの接続数が非常に多いか、キャッシュの削減設定が厳しすぎることを示しています (厳しすぎる場合、ブックはすぐにアンロードされ、システムから削除されますが、そのデータに対する要求はアクティブな状態のままになります)。 偽陽性をカウントしないようにするには、4 時間あたりの接続数が 20 以上の場合に比率を計算する必要があります。 この正常性ルールは、別の比率に基づいて構成できます。 詳細については、「[Power Pivot の正常性ルールの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md)」を参照してください。 キャッシュの構成については、「[ディスクの使用領域の構成 (PowerPivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint.md)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: Logs ディレクトリでプログラムのクラッシュを示す 1 つ以上のミニダンプ ファイルが見つかりました。|いいえ|いいえ|SharePoint 2013<br /><br /> SharePoint 2010|プログラムのクラッシュ時に、クラッシュする直前の [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの状態に関する情報を記録したミニダンプ ファイルが生成されます。 この情報はマイクロソフトに送信したり、トラブルシューティングに使用したりできます。 このルールは、.dmp ファイルがサーバーで検出された場合にトリガーされます。 このルールでは、ファイルへのリンクが提供されます。このリンクは、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint インスタンスの \OLAP\Log フォルダーにあります。 テキスト エディターを使用して、ファイルの内容を表示することはできません。 ミニダンプ ファイルを表示するには、デバッグ ツールを別途ダウンロードしてインストールする必要があります。 詳細については、「 [Windows 用デバッグ ツールのダウンロードとインストール](http://go.microsoft.com/fwlink/?linkID=208266)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] データがキャッシュされるドライブのディスク領域が不足しています。|はい|いいえ|SharePoint 2010|既定では、バックアップ フォルダーが置かれているディスク ドライブ上のディスク領域が 5% 未満になると、この正常性ルールがトリガーされます。 この割合の設定方法の詳細については、「[Power Pivot の正常性ルールの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md)」を参照してください。 ディスクの使用については、「 [ディスクの使用領域の構成 &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint.md)をクリックします。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: 使用状況データが必要な頻度で更新されていません。|はい|いいえ|SharePoint 2013<br /><br /> SharePoint 2010|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint では、組み込みの使用状況データ収集システムを使用して、接続、データ更新、およびクエリ応答時間に関するメトリックを収集します。 この使用状況データを [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーション データベースに格納し、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードのレポートにデータを提供する[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブック ( [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] Management Data.xlsx) を更新します。 このルールは、使用状況データが十分な頻度で [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] Management Data.xlsx ファイルに移動されていないことを示します。 このルールでは、ファイルが更新されている証拠として .xlsx ファイルのタイムスタンプを使用します。 データの正確性を損なう他の問題が使用状況データ収集システムにある場合、その問題はこのルールでは検出されません。 このエラーのトラブルシューティングを実行するには、タイマー ジョブが実行されていることを確認します。 使用状況データ コレクションに関する詳細については、「[使用状況データ収集の構成 &#40;PowerPivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: MidTier プロセス アカウントは、関連付けられているすべての SPWebApplication に対して 'すべて読み取り' 権限を持っている必要があります。|いいえ|はい|SharePoint 2013<br /><br /> SharePoint 2010|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの ID は、ドキュメントに対する "表示のみ" 権限を持つユーザーに代わって SharePoint コンテンツ データベースにアクセスするために、" **すべて読み取り** " 権限を持っている必要があります。<br /><br /> [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの ID として使用されるアカウントを特定するには、サーバーの全体管理で **[サービス アカウントの構成]** ページを開きます。 通常、サービス アプリケーションは、 **SharePoint Web サービスのシステム** のサービス アプリケーション プールまたは専用のアプリケーション プールで実行されます。<br /><br /> このルールには、 **[自動修復する]** オプションがありますが、権限を手動で付与したほうがよい結果が得られます。<br /><br /> <br /><br /> 1) サーバーの全体管理で、 **[Web アプリケーションの管理]** をクリックします。<br /><br /> 2) Web サイトを選択し、 **[ユーザー ポリシー]** をクリックします。<br /><br /> 3) **[ユーザーの追加]** をクリックします。<br /><br /> 4) [(すべての領域)] を選択し、 **[次へ]** をクリックします。<br /><br /> 5) [ユーザー] には、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの ID を入力し、 **[すべて読み取り]** チェック ボックスをオンにします。 6) **[完了]** をクリックします。<br /><br /> 6) 修復を確認します。 [監視] で、 **[ルール定義の確認]** をクリックします。 検索し、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ルールを開きます。 **[今すぐ実行]** をクリックします。 **[問題とソリューションの確認]** に戻り、ルールが表示されないことを確認します。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: セカンダリ ログオン サービス (seclogon) は無効になっています。|いいえ|いいえ|SharePoint 2013<br /><br /> SharePoint 2010|セカンダリ ログオン サービスは、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ギャラリーの [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックのサムネイル画像を生成するために使用されます。 既定では、セカンダリ ログオン サービスは手動スタートアップに設定されています。 サービスが無効になっている場合、サムネイルの生成は失敗します。 また、ULS ログに "エラー 1058 の根本原因として、"セカンダリ ログオン" Windows サービスが無効になっている可能性があります。" というエラー メッセージが含まれます。<br /><br /> サービス構成を確認するには、サービス コンソール アプリケーションを使用してセカンダリ ログオンを検索し、 **[スタートアップの種類]** を **[手動]** に変更します。 サービスを有効にできない場合は、組織でこのサービスを無効にするグループ ポリシーが適用されている可能性があります。 管理者に連絡して、これに該当するかどうかを確認してください。<br /><br /> サービスを有効にすると、サムネイルまたはスナップショットの画像が経時的に更新されます。 必要に応じて、サービスを再起動し、特定のレポートのプロパティ ページを開いて再保存することで、強制的に更新することもできます。 詳細については、「 [Power Pivot ギャラリーを使用する方法](http://go.microsoft.com/fwlink/?LinkId=246462)」を参照してください。|  
|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]: サーバーの全体管理用に構成されているスタンドアロン WFE に ADOMD.NET がインストールされていません。|いいえ|いいえ|SharePoint 2013<br /><br /> SharePoint 2010|ADOMD.NET は、Analysis Services データベースへの接続をサポートする Analysis Services クライアント ライブラリです。 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint の配置では、ADOMD.NET を使用して、サーバーの全体管理で [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードの組み込みレポートにアクセスできます。 組み込みレポートは、実際には、埋め込み Analysis Services のデータが含まれた [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] ブックです。 管理ダッシュボードでは、ADOMD.NET を使用して、ブックに含まれているデータを読み込むサーバーに接続要求を送信します。<br /><br /> スタンドアロン Web フロントエンド サーバーで実行されているサーバーの全体管理を含むトポロジで、管理ダッシュボードにこれらのレポートを表示する場合は、ADOMD.NET を手動でインストールする必要があります。 詳細については、「 [サーバーの全体管理を実行している Web フロントエンド サーバーに ADOMD.NET をインストールする方法](http://msdn.microsoft.com/en-us/c2372180-e847-4cdb-b267-4befac3faf7e)」を参照してください。|  
  
  