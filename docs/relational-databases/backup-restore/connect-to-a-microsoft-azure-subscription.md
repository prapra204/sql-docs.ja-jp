---
title: Microsoft Azure サブスクリプションへの接続 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cca5a270-643f-4677-8802-98464f19f82a
caps.latest.revision: 4
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: 78be8dddc2a8d2afc4728280a9f0e1cb618b8d3e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917467"
---
# <a name="connect-to-a-microsoft-azure-subscription"></a>Microsoft Azure サブスクリプションへの接続
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
**Microsoft サブスクリプションへの接続** を使用して、既存の Azure BLOB コンテナーを SQL Server のインスタンスに登録します。  ダイアログ ボックスでは、Shared Access Signature と格納されたアクセス ポリシーが Azure BLOB コンテナーに作成された後に、SQL Server 資格情報が作成されます。  このダイアログ ボックスは、SQL Server Management Studio からバックアップ タスクまたは復元タスクを使用する際に表示され、その操作には URL デバイスが必要です。

## <a name="limitation"></a>制限事項
**Microsoft サブスクリプションへの接続** は、Service Management (クラシック) デプロイメント モデルを使って作成された Azure Storage アカウントでのみ機能します。  Azure デプロイメント モデルに関する詳細については、「 [Azure Resource Manager とクラシック デプロイ](https://azure.microsoft.com/en-us/documentation/articles/resource-manager-deployment-model/)」を参照してください。

## <a name="options"></a>および
**サインイン**     
適切な Azure アカウントでサインインします。

**使用するサブスクリプションの選択**      
ドロップダウン リストから目的のサブスクリプションを選択します。

**ストレージ アカウントの選択**  
ドロップダウン リストからストレージ アカウントを選択します。

**BLOB コンテナーの選択**   
ドロップダウン リストから目的の BLOB コンテナーを選択します。

**Shared Access Policy の有効期限**   
Shared Access Policy は、指定された日付に期限が切れます。  既定の有効期限の日付は、作成日から 1 年後です。  必要に応じて変更します。

**生成された Shared Access Signature**   
生成された Shared Access Signature は、リッチ テキスト ボックスに表示されます。

**資格情報の作成**   
ボタンを使って、格納されたアクセス ポリシーおよび Shared Access Signature が生成された後に SQL Server 資格情報が作成されます。
