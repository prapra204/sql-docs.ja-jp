---
title: Azure Resource Manager 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: connection-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
caps.latest.revision: 3
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.openlocfilehash: ff84bc71b527ad08f51e22097d6631aa8aa8d1cc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="azure-resource-manager-connection-manager"></a>Azure Resource Manager 接続マネージャー
**Azure Resource Manager 接続マネージャー**により、SSIS パッケージは[サービス プリンシパル](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)を使って Azure リソースを管理できます。

**Azure Resource Manager 接続マネージャー**は、[SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) のコンポーネントです。

**Azure Resource Manager 接続マネージャー**を作成して構成するには、以下の手順のようにします。

1. **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureResourceManager]** を選び、**[追加]** をクリックします。
2. **[Azure Resource Manager Connection Manager Editor]\(Azure Resource Manager 接続マネージャー エディター\)** ダイアログ ボックスで、サービス プリンシパルの **[Application ID]\(アプリケーション ID\)**、**[Application Key]\(アプリケーション キー\)**、**[Tenant ID]\(テナント ID\)** を指定します。 これらのプロパティについて詳しくは、[こちら](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)の記事をご覧ください。
3. **[OK]** をクリックして、ダイアログ ボックスを閉じます。
4. 作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。
