---
title: .dqs ファイルへのナレッジ ベースのエクスポート | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.component: data-quality-services
ms.reviewer: ''
ms.suite: sql
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a324ead5-c8aa-4e26-abe3-ef415add00f8
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4d203ed9eb7c3bdf848eb74fa1be56dd63e27438
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="export-a-knowledge-base-to-a-dqs-file"></a>.dqs ファイルへのナレッジ ベースのエクスポート

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) で .dqs データ ファイルにナレッジ ベース全体をエクスポートする方法について説明します。 ドメインまたはナレッジ ベース全体をデータ ファイルにエクスポートできます。 ドメインのエクスポートについては、「[.dqs ファイルへのドメインのエクスポート](../data-quality-services/export-a-domain-to-a-dqs-file.md)」をご覧ください。  
  
 ナレッジ ベースを .dqs ファイルにエクスポートし、後で別のナレッジ ベースとしてインポートすることで、ナレッジの生成処理を簡略化し、時間と労力を節約します。 ナレッジ ベースやその中のナレッジを他のユーザーと共有できます。 .dqs ファイルには、ドメインや照合ポリシーを含むナレッジ ベースのすべての情報が含まれます。ただし、アタッチされた参照データ情報は含まれません。 .dqs ファイルをインポートした後、必要に応じて、必要なドメインを適切な参照データ サービスに再度アタッチします。 ナレッジ ベース内の発行済みのデータと発行されていないデータの両方がエクスポートされます。  
  
 エクスポート処理で作成された .dqs データ ファイルは暗号化されるため、内容を表示することはできません。  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Prerequisites"></a> 前提条件  
 ナレッジ ベースを .dqs データ ファイルにエクスポートするには、ナレッジ ベースを作成して開いておく必要があります。 エクスポート先の .dqs ファイルを用意する必要はありません。1 .dqs ファイルは作成されます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 ナレッジ ベースを .dqs データ ファイルにエクスポートするには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールが必要です。  
  
##  <a name="Export"></a> Export a knowledge base to a .dqs file  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、ドメイン管理アクティビティ内のナレッジ ベースを開きます。  
  
3.  [ドメイン管理] ページで (任意のタブを選択し)、ドメイン リストの上にある **[ナレッジ ベース データをエクスポートします]** アイコンをクリックして、 **[ナレッジ ベースのエクスポート]** をクリックします。 または、 **[ドメイン]** リスト内で右クリックして **[エクスポート]** にマウス ポインターを合わせ、 **[ナレッジ ベースのエクスポート]** をクリックします。  
  
4.  **[データ ファイルにエクスポート]** ダイアログ ボックスで、ファイルを保存するフォルダーに移動し、ファイルに名前を付けるかナレッジ ベース名のままにし、**[ファイルの種類]** を **[DQS データ ファイル (\*.dqs)]** のままにして、**[保存]** をクリックします。  
  
5.  **[ナレッジ ベースのエクスポート]** ダイアログ ボックスで、ステータス行にエクスポートの完了が表示されていることを確認します。 **[OK]** をクリックします。  
  
##  <a name="FollowUp"></a> 補足情報: ドメインを .dqs ファイルにエクスポートした後  
 ナレッジ ベースを .dqs ファイルにエクスポートした後で、そのナレッジ ベースを (新しい名前で) 同じ [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] にインポートしたり、異なる [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]にインポートしたりできます。  
  
  
