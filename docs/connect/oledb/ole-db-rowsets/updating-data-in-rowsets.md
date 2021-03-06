---
title: 行セットのデータの更新 |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用して行セットのデータの更新
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, updating data
- OLE DB Driver for SQL Server, data updates
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3c5d70a1d582330f935798887fd37d81d097bc2a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="updating-data-in-rowsets"></a>行セット内のデータの更新
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQL Server 更新プログラムの OLE DB Driver[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ コンシューマーがそのデータを含む変更可能な行セットを更新するとします。 コンシューマーがいずれかのサポートを要求したときに、可能な行セットが作成された、 **IRowsetChange**または**IRowsetUpdate**インターフェイスです。  
  
 すべて OLE DB Driver for SQL Server が変更可能な行セットを使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]行セットをサポートするカーソル。 行セット プロパティ DBPROP_LOCKMODE は、カーソルでの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の同時実行制御動作を変更し、更新可能な行セット内の行をフェッチする動作や、その行セット内のデータの整合性に関するエラーを生成する動作を決定します。  
  
 SQL Server の OLE DB Driver は前に、または更新後の行の同期をサポートします。  
  
> [!NOTE]  
>  IRowChange::SetColumns を使用して、行オブジェクトの 1 つ以上の名前付き列の値を設定できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Server カーソルでのデータ更新](../../oledb/ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [行の再同期](../../oledb/ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
