---
title: sys.dm_os_process_memory (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_process_memory_TSQL
- dm_os_process_memory_TSQL
- dm_os_process_memory
- sys.dm_os_process_memory
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_process_memory dynamic management view
ms.assetid: e838130c-95d4-4605-9e3b-eb0ab71cd250
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5732a15fe8fe2d30f6f9c693e66258c0de4b44d3
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmosprocessmemory-transact-sql"></a>sys.dm_os_process_memory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス空間から生じる大半のメモリ割り当ては、こうした割り当ての追跡と管理を可能にするインターフェイスを通じて制御されます。 ただし、メモリ割り当てが、内部のメモリ管理ルーチンをバイパスする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アドレス空間で実行される場合もあります。 値は、ベースとなるオペレーティング システムを通じて取得されます。 操作することがない内部メソッドによって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と調整を行うロックやラージ ページ割り当てを除き、します。  
  
 戻り値のメモリ サイズは常にキロバイト (KB) 単位で表されます。 列**total_virtual_address_space_reserved_kb**の複製である**virtual_memory_in_bytes**から**sys.dm_os_sys_info**です。  
  
 次の表は、プロセス アドレス空間の全体像を表したものです。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_process_memory**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**physical_memory_in_use_kb**|**bigint**|オペレーティング システムから報告されたプロセス ワーキング セットに、ラージ ページ API を使用して追跡された割り当てを加えた値 (KB 単位) を示します。 Null を許容しません。|  
|**large_page_allocations_kb**|**bigint**|ラージ ページ API を使用して割り当てられた物理メモリを指定します。 Null を許容しません。|  
|**locked_page_allocations_kb**|**bigint**|メモリ内でロックされているメモリ ページを指定します。 Null を許容しません。|  
|**total_virtual_address_space_kb**|**bigint**|仮想アドレス空間のユーザー モード領域の合計サイズを示します。 Null を許容しません。|  
|**virtual_address_space_reserved_kb**|**bigint**|プロセスによって予約された仮想アドレス空間の総量を示します。 Null を許容しません。|  
|**virtual_address_space_committed_kb**|**bigint**|コミットまたは物理ページへのマップが済んでいる、予約済みの仮想アドレス空間の量を示します。 Null を許容しません。|  
|**virtual_address_space_available_kb**|**bigint**|現在利用可能な仮想アドレス空間の量を示します。 Null を許容しません。<br /><br /> **注:** 割り当ての粒度が存在できるよりも小さいする領域を解放します。 これらの領域は割り当てに利用できません。|  
|**page_fault_count**|**bigint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスに起因するページ違反の数を示します。 Null を許容しません。|  
|**memory_utilization_percentage**|**int**|ワーキング セット内のコミット済みメモリの割合を指定します。 Null を許容しません。|  
|**available_commit_limit_kb**|**bigint**|プロセスによってコミット可能なメモリの量を示します。 Null を許容しません。|  
|**process_physical_memory_low**|**bit**|プロセスが物理メモリの不足の通知に応答していることを示します。 Null を許容しません。|  
|**process_virtual_memory_low**|**bit**|仮想メモリ不足の条件が検出されたことを示します。 Null を許容しません。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


