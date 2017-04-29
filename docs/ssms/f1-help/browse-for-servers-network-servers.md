---
title: "[サーバーの参照] ([ネットワーク サーバー]) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0dfaef0364cf72e994b0fe5de778adc8a18bd715
ms.lasthandoff: 04/11/2017

---
# <a name="browse-for-servers-network-servers"></a>[サーバーの参照] ([ネットワーク サーバー])
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] コンポーネントに接続する際に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インスタンスの正確な名前がわからない場合は、**[サーバー名]** ボックスで **[参照]** をクリックして **[サーバーの参照]** ダイアログ ボックスを開きます。  
  
サーバー コンピューターの [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser サービスによって、このダイアログ ボックスの内容が自動入力されます。 インスタンス名が一覧に表示されない場合は、次のような原因が考えられます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] を実行しているコンピューターで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Browser サービスが実行されていない。  
  
-   ファイアウォールにより、UDP ポート 1434 がブロックされている。  
  
-   **HideInstance** フラグが設定されている。  
  
一覧に表示されないインスタンスに接続するには、TCP/IP ポート番号または名前付きパイプのパイプ名を含む、そのインスタンスの完全な接続文字列を入力します。  
  
## <a name="options"></a>オプション  
**[接続に使用する、ネットワーク内の SQL Server インスタンスを選択します]**  
ツリーに表示された [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インスタンスをクリックして、接続するサーバーを指定します。 **+** または **–** 記号の付いたノードをクリックすることにより、ツリーの一部を表示または非表示にすることができます。  
  
