---
title: "Power BI アーカイブ済みワークスペース"
description: "Office 365 テナントを管理した後の Power BI アーカイブ済みワークスペース"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 06/28/2017
ms.author: asaxton
ms.openlocfilehash: e321fc33eb32988c358ac87290150fe54c1e9479
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2017
---
# <a name="power-bi-archived-workspace"></a>Power BI アーカイブ済みワークスペース
Power BI では、だれでもサインアップすれば、数分でサービスを使い始めることができます。  後から組織の IT 部門が、組織内のユーザーから Power BI の管理を引き継ぐことができます。  この引き継ぎが行われる場合、組織内のユーザーとアクセス許可の中央管理を活用し、組織の他のサービスで使うのと同じユーザー名とパスワードを使って、効率的なサインインを利用できます。 

IT 部門が Power BI の管理を始める前に作成されたコンテンツは、Power BI アーカイブ済みワークスペースに配置されます。これは、[Power BI](https://app.powerbi.com) の左側のナビゲーションからアクセスできます。  セキュリティで保護され、組織の IT 部門によって管理される新しい Power BI コンテンツは、マイ ワークスペースで作成し始めてください。  アーカイブ済みワークスペースは引き続き存在しますが、アーカイブ済みワークスペースのコンテンツに対して実行できるアクションは制限されます。  これらの制限を取り除くには、アーカイブ済みワークスペースから、IT 部門によって管理されるマイ ワークスペースに、コンテンツを移行する必要があります。

## <a name="restrictions-in-your-archived-workspace"></a>アーカイブ済みワークスペースの制限
アーカイブ済みワークスペースからコンテンツが削除されることはありません。  データの取得、レポートやダッシュボードの作成、データセットの更新を引き続き行うことができます。  あなたがコンテンツを共有した相手の既存ユーザーも、アーカイブ済みワークスペース内のコンテンツを見ることができます。

ただし、アーカイブ済みワークスペース内のコンテンツには、以下のようないくつかの制限があります。

* **OneDrive for Business。**  アーカイブ済みワークスペース内のデータセットに対して、OneDrive for Business からデータの取得や更新ができなくなります。  このソースに接続しようとすると、警告が表示されます。
* **ダッシュボードの共有。**  アーカイブ済みワークスペースから、他のユーザーとダッシュボードを共有することはできません。  既にアクセス権を持つユーザーは、アーカイブ済みワークスペースにアクセスすることによって、共有されたダッシュボードを引き続き見ることができます。
* **グループの作成。**  アーカイブ済みワークスペースにグループを作成することはできません。
* **Power BI モバイル アプリでのアクセス。**  アーカイブ済みワークスペースにあるコンテンツを Web で引き続き見ることはできますが、Power BI モバイル アプリでは表示されなくなります。

## <a name="migrating-content-in-your-archived-workspace"></a>アーカイブ済みワークスペースのコンテンツの移行
Power BI を引き続き利用する場合、IT 部門によって管理される新しいコンテンツは、マイ ワークスペースで作成してください。   また、アーカイブ済みワークスペースのすべてのコンテンツをマイ ワークスペースに移行する必要があります。  コンテンツを移行する方法は、コンテンツの種類によって異なります。

* **Excel または Power BI Desktop のデータセット。**  アーカイブ済みワークスペースからマイ ワークスペースに切り替え、[マイ データ] ボタンをクリックして、Excel または Power BI Desktop のファイルを再アップロードすることによって、これらのデータセットを移行します。  スケジュールされた更新が設定されている場合、マイ ワークスペースの新しいデータセットに対して設定しなおす必要があります。
* **その他のデータセット。**  マイ ワークスペースに切り替えて、[データの取得] ボタンをクリックすると、アーカイブ済みワークスペースで作成された他のデータセットに再接続できます。  セキュリティ情報や接続情報を再入力することが必要な場合があります。
* **レポート。**  Excel ファイルや Power BI Desktop ファイルに含まれていたレポート、またはコンテンツ パックの一部としてインストールされたレポートは、対応する Excel または Power BI Desktop のファイルを再びアップロードするか、コンテンツ パックに再接続することで、自動的に再作成されます。  Power BI サービスを通じて独自のレポートを作成した場合、マイ ワークスペースでこれらのレポートを作成しなおす必要があります。
* **ダッシュボード。**  コンテンツ パックの一部としてインストールされたダッシュボードは、ユーザーがマイ ワークスペースのコンテンツ パックに再接続すると、自動的に再作成されます。  Power BI サービスを通じて独自のダッシュボードを作成した場合、マイ ワークスペースでこれらのダッシュボードを作成しなおす必要があります。

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](http://community.powerbi.com/)。
