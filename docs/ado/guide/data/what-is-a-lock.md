---
title: ロックとは何ですか。 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], locking
- locks [ADO], about locking
ms.assetid: f8989555-28c6-4c17-9bf8-7f44a8a5c407
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 396faecd122eef7ad6e40f790252a0902a508ba8
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273291"
---
# <a name="what-is-a-lock"></a>ロックとは何ですか。
ロックは、DBMS が、マルチ ユーザー環境での行にアクセスを制限するプロセスです。 行または列が排他的にロックとロックが解放されるまでロックされたデータにアクセスする他のユーザーを作成できません。 これにより、2 人のユーザーが行の同じ列を同時に更新できません。  
  
 ロックは、リソースの観点から非常に高くなる可能性がや、データの整合性を保持するために必要な場合にのみ使用する必要があります。 ここで数百または数千のユーザーでしたしようとして毎秒のレコードにアクセス データベースの — インターネットに接続されているデータベースなど — 不要なロックが直ちにアプリケーションのパフォーマンスの低下を招きます。  
  
 どのデータ ソースと ADO カーソル ライブラリ、この同時実行を適切なロック オプションを選択して管理を制御できます。  
  
 設定、 **LockType**プロパティを開く前に、**レコード セット**を開くときにプロバイダーのロックの種類を使用する必要がありますを指定します。 開いている上で使用されているロックの種類を取得するプロパティを読み取る**Recordset**オブジェクト。  
  
 プロバイダーが、すべてのロックの種類をサポートしていません。 プロバイダーをサポートして、要求された場合**LockType**設定すると、別の種類のロックが代用されます。 使用可能な実際のロック機能を決定する、**レコード セット**オブジェクトを使用して、[サポート](../../../ado/reference/ado-api/supports-method.md)メソッドを**adUpdate**と**adUpdateBatch**.  
  
 **AdLockPessimistic**場合の設定はサポートされていません、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティに設定されている**adUseClient です。** サポートされていない値が設定されている場合は、エラーは発生しません。サポートされている最も近い**LockType**が使用されます。  
  
 **LockType**プロパティが読み取り/書き込み時に、 **Recordset**が開いているときは、終了、および読み取り専用です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ロックの種類](../../../ado/guide/data/types-of-locks.md)
