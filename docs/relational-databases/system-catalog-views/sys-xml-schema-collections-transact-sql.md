---
title: sys.xml_schema_collections (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_collections_TSQL
- sys.xml_schema_collections
- xml_schema_collections
- xml_schema_collections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_collections catalog view
ms.assetid: f3f7f3dc-029f-4942-ab3c-75fa9814e40f
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 11e9a91fc27b704b54415acfe98a516a2176603a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33221153"
---
# <a name="sysxmlschemacollections-transact-sql"></a>sys.xml_schema_collections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  XML スキーマ コレクションごとに 1 行のデータを返します。 XML スキーマ コレクションは、名前付きの XSD 定義セットです。 XML スキーマ コレクション自体はリレーショナル スキーマに含まれ、スキーマ スコープの [!INCLUDE[tsql](../../includes/tsql-md.md)] 名で識別されます。 xml_collection_id、schema_id、および name の組は一意です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|xml_collection_id|**int**|XML スキーマ コレクションの ID。 データベース内で一意です。|  
|schema_id|**int**|XML スキーマ コレクションを含むリレーショナル スキーマの ID。|  
|principal_id|**int**|スキーマの所有者と異なる場合は、個々 の所有者の ID です。 既定では、スキーマに含まれるオブジェクトは、スキーマの所有者によって所有されます。 ただし、所有権を変更する ALTER AUTHORIZATION ステートメントを使用して、別の所有者を指定することがあります。<br /><br /> NULL = 別の所有者はありません。|  
|name|**sysname**|XML スキーマ コレクションの名前。|  
|create_date|**datetime**|XML スキーマ コレクションが作成された日付。|  
|modify_date|**datetime**|XML スキーマ コレクションが最後に変更された日付。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML スキーマ&#40;XML 型システム&#41;カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
