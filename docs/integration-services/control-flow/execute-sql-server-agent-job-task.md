---
title: "SQL Server エージェント ジョブ実行タスク |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.executesqlserveragentjobtask.f1
helpviewer_keywords:
- Execute SQL Server Agent Job task [Integration Services]
- jobs [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 65caffce1a119757743f8f2d6bf708112492e767
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="execute-sql-server-agent-job-task"></a>SQL Server エージェント ジョブの実行タスク
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの実行タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを実行します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、SQL Server のインスタンスで定義されたジョブを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows サービスです。 ユーザーは、Transact-SQL ステートメントや ActiveX スクリプトの実行、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] やレプリケーションのメンテナンス タスクの実行、およびパッケージの実行を行うジョブを作成できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を監視し、警告を発するジョブを構成することもできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブは、通常、繰り返し実行するタスクの自動化に使用します。 詳細については、 [「ジョブの実装」](http://msdn.microsoft.com/library/69e06724-25c7-4fb3-8a5b-3d4596f21756)を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの実行タスクを使用すると、パッケージは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントに関連する管理タスクを実行できます。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブでは、フォルダー内のパッケージの一覧を取得する **sp_enum_dtspackages** などのシステム ストアド プロシージャを実行できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ローカルまたはマルチ サーバー管理ジョブが自動的に実行する前に、エージェントを実行する必要があります。  
  
 このタスクは、 **sp_start_job** システム プロシージャをカプセル化し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの名前を引数としてこのプロシージャに渡します。 詳細については、[「sp_start_job (Transact-SQL)」](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md) を参照してください。  
  
## <a name="configuring-the-execute-sql-server-agent-job-task"></a>SQL Server エージェント ジョブの実行タスクの構成  
 プロパティは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。 このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../includes/ssis-md.md)] に表示されます。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。  
  
-   [[SQL Server エージェント ジョブの実行タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  