---
title: ドメイン管理 - 分析プラットフォーム システムを作成 |Microsoft ドキュメント
description: 一部の操作では、Analytics Platform System ドメイン管理者特権が必要です。 これには、ドメイン管理者の追加のアプライアンスを作成する方法について説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 73eff52cb6e583383f13334e78012721a20a3e25
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31545118"
---
# <a name="create-an-aps-domain-administrator"></a>APS ドメイン管理者を作成します。
一部の操作では、Analytics Platform System ドメイン管理者特権が必要です。 これには、ドメイン管理者の追加のアプライアンスを作成する方法について説明します。  
  
## <a name="create-a-domain-administrator"></a>ドメイン管理者を作成します。  
APS のすべてのノードを実行するユーザーを構成する十分なアクセス許可、 **APS Configuration Manager** (`dwconfig.exe`) のメンバーである必要があります、 **Domain Admins**グループ。 ユーザーを開始および APS サービスを停止のメンバーである必要があります、 **PdwControlNodeAccess**グループ。  
  
#### <a name="to-add-a-user-to-the-domain-admins-group"></a>Domain Admins グループにユーザーを追加するには  
  
1.  アクティブな AD ノードへのログイン **(*appliance_domain*-AD01**または ***appliance_domain *-AD02**) 既存のアプライアンス ドメイン管理者アカウントを使用します。  
  
2.  [スタート] メニューの **[ファイル名を指定して実行]** をクリックします。 **開く**ボックスに、入力**dsa.msc**です。 **[OK]** をクリックします。  
  
3.  **Active Directory ユーザーとコンピューター**プログラムを右クリックして**ユーザー**、 をポイント**新規**、クリックして**ユーザー**です。  
  
4.  **新しいオブジェクト-ユーザー**  ダイアログ ボックスは、新しいユーザーの説明を完了し、をクリックして**次**です。  
  
    パスワード ダイアログ ボックスを完了し、をクリックして**次**です。  
  
    > [!WARNING]  
    > SQL Server PDW はサポートされていません、ドル記号 ($) は、ドメイン管理者またはローカル管理者パスワード。 ドル記号を含むパスワードは有効なと使用できるようにするが、アップグレードおよびメンテナンス アクティビティをブロックすることができます。  
  
    新しいユーザーの説明を確認し、をクリックして**完了**です。  
  
5.  ユーザーの一覧で、新しいユーザーを開くには、ユーザーのプロパティ ダイアログ ボックスをダブルクリックします。  
  
6.  **メンバーの** タブで、をクリックして**追加**です。  
  
    型**Domain Admins です。PdwControlNodeAccess**  をクリックし、**名前の確認**です。 **[OK]** をクリックします。  
  
    新しいユーザーを追加、 **Domain Admins**グループおよび**PdwControlNodeAccess**グループ。 **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
[構成マネージャーを起動&#40;分析プラットフォーム システム&#41;](launch-the-configuration-manager.md)  
  
