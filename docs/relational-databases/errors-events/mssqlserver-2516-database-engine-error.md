---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c42dd135eace8e81b2423e2e70e4c09eb6baf1b0
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver2516"></a>MSSQLSERVER_2516
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2516|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_REPAIR_DIFF_MAP_INVALIDATED|  
|メッセージ テキスト|修復により、データベース NAME の差分ビットマップが無効になりました。 差分バックアップ チェーンが壊れています。 データベース全体をバックアップしてから、差分バックアップを実行できます。|  
  
## <a name="explanation"></a>説明  
この情報メッセージは、エラー MSSQLEngine_2515 の修復時に返されます。  
  
## <a name="user-action"></a>ユーザーの操作  
データベースの完全バックアップを実行します。  
  
## <a name="see-also"></a>参照  
[データベースの完全バックアップの作成 &#40;SQL Server&#41;](~/relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
