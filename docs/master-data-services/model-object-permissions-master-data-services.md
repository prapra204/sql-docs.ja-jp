---
title: モデル オブジェクト アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
caps.latest.revision: 9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: a5a842352e1c6e1421b0d796d8b29a8a83d22366
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="model-object-permissions-master-data-services"></a>モデル オブジェクト権限 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  モデル オブジェクト権限は必須です。 これにより、UI の **[エクスプローラー]** 機能領域でユーザーがアクセスできる属性が決まります。  
  
 たとえば、ユーザーに Product エンティティに対する **更新** 権限を割り当てると、ユーザーは Product エンティティのすべての属性を更新できます。 単一の属性に対する **更新** 権限を割り当てた場合は、ユーザーはその属性のみを更新できます。  
  
 個別の各属性値に割り当てられるセキュリティを決定するため、モデル オブジェクト権限は階層メンバー権限と組み合わされて、ユーザーがアクセスできるメンバーが決定されます。  
  
 **[エクスプローラー]** 以外の機能領域へのアクセス権限をユーザーに付与するには、ユーザーはモデル管理者である必要があります。これには、オブジェクト モデルでの管理権限の割り当ても含まれます。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
 モデル オブジェクト権限は、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]のユーザー インターフェイス (UI) を使用して、**[ユーザー/グループの権限]** 機能領域の **[モデル]** タブで割り当てられます。このタブでは、モデルがツリー構造として表されます。 ツリー内のオブジェクトに権限を割り当てると、下位にあるすべてのオブジェクトがその権限を継承します。 継承を無効にするには、個々のオブジェクトに権限を割り当てます。  
  
 読み取り、作成、更新、削除、拒否などの権限を組み合わせてモデル オブジェクトに割り当てることができます。 **[モデル]** タブで権限を割り当てない場合、ユーザーは [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でモデルおよびデータを表示できません。  
  
## <a name="best-practice"></a>推奨事項  
 一般に、 **すべての** 権限をモデル オブジェクトに割り当てた後、その下にあるオブジェクトに権限を明示的に割り当てる必要があります。  
  
## <a name="external-resources"></a>外部リソース  
 msdn.com のブログ投稿「 [Security Improvements (セキュリティの向上)](http://go.microsoft.com/fwlink/p/?LinkId=615376)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限を割り当てる (マスター データ サービス)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [モデル アクセス許可 (マスター データ サービス)](../master-data-services/model-permissions-master-data-services.md)   
 [機能領域アクセス許可 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)   
 [階層メンバーの権限 (マスター データ サービス)](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [権限の決定方法 (マスター データ サービス)](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
