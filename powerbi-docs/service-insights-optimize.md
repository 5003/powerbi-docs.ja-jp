---
title: Power BI クイック インサイト用のデータの最適化
description: Power BI クイック インサイト用のデータを最適化します。 Power BI でデータの詳細情報を見つけられない場合、実行できることを説明しています。
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2017
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: fbf49a9ddbec5f087a28e51144c782e2f1739db0
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/21/2018
ms.locfileid: "46546947"
---
# <a name="optimize-your-data-for-power-bi-quick-insights"></a>Power BI クイック インサイト用のデータの最適化
クイック インサイトの結果を改善する必要がありますか。  データセット所有者の場合は、以下を試します。

* データセットの列を表示または非表示にします。 Power BI クイック インサイトでは、非表示の列は検索されません。  そのため、重複する列や不要な列を非表示にして、興味のある列を表示します。
* 名前、時刻、日付、数値などのさまざまなデータの種類を組み合わせて使用します。
* 情報が重複している列を避けます (非表示にします)。  これは、意味のあるパターンの検索から貴重な時間を奪います。  たとえば、ある列に状態名を略さずに含め、別の列に省略名を含めるなどです。
* データが統計的に有意でないことを示すエラー メッセージが表示される場合があります。  これは、ごく単純なモデルやデータが少ないモデル、日付または数値の列がないモデルの場合に発生することがあります。 インサイトを生成するには、データセットに少なくとも 1 つのディメンションと 1 つのメジャーが必要です。

### <a name="next-steps"></a>次の手順
[Power BI クイック インサイト](consumer/end-user-insights.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

