---
title: URL を使用して Power BI レポート パラメーターを追加する
description: URL クエリ文字列パラメーターを使って、レポートをフィルター処理します。複数のフィールドでもフィルター処理できます。
author: mihart
ms.author: mihart
manager: annebe
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 09/14/2018
LocalizationGroup: Reports
ms.openlocfilehash: 1124163b985f575df08a9ba4f065c6a6b1abf54c
ms.sourcegitcommit: cca21f8089e71b595d3aca30c95f12e4bbf767cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2018
ms.locfileid: "45626033"
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>URL のクエリ文字列パラメーターを使用してレポートをフィルター処理する

Power BI サービスでレポートを開くと、レポートの各ページに一意の URL があります。 そのレポート ページをフィルター処理するには、レポート キャンバスの [フィルター] ウィンドウを使うことができます。  または、クエリ文字列パラメーターを URL に追加して、レポートを事前にフィルター処理できます。 同僚に見せるレポートに事前にフィルターを適用したい場合、 1 つの方法は、レポートの既定の URL にフィルター パラメーターを追加し、新しい URL 全体をメールで同僚に送るというものです。

![サービスでの Power BI のレポート](media/service-url-filters/power-bi-report2.png)

## <a name="uses-for-query-string-parameters"></a>クエリ文字列パラメーターの用途

たとえば、Power BI Desktop で作業しているときに、他の Power BI レポートへのリンクを含むレポートを作成しますが、他のレポートには一部の情報のみを表示するとします。 最初に、クエリ文字列パラメーターを使用してレポートをフィルター処理し、URL を保存します。 次に、Desktop でこれらの新しいレポート URL を使用してテーブルを作成します。  その後、レポートを発行して共有します。

また、クエリ文字列パラメーターは、高度な Power BI ソリューションを作成するユーザーが使用することもできます。  そのユーザーは DAX を使用して、現在のレポートでの顧客の選択に基づいて、フィルター処理されたレポート URL を動的に生成するレポートを作成します。 顧客が URL を選択すると、目的の情報のみが表示されます。 

## <a name="query-string-parameter-syntax-for-filtering"></a>フィルター処理のためのクエリ文字列パラメーターの構文

パラメーターを使用すれば、値にスペースや特殊文字が含まれている場合でも、レポートで 1 つ以上の値をフィルター処理することができます。 基本構文はとても簡単です。レポート URL に疑問符を追加し、その後にフィルター構文を追加します。

URL?filter=***<テーブル>***/***<フィールド>*** eq '***<値>***'

![フィルターを含む URL](media/service-url-filters/power-bi-filter-urls7b.png)

* **テーブル**と**フィールド**の名前では大文字と小文字が区別されますが、**値**では区別されません。
* レポート ビューに表示されないフィールドをフィルター処理することもできます。

### <a name="field-types"></a>フィールドの型

フィールドの型は、数値、日付時刻、または文字にすることができます。使用する型は、データセットに設定されている型と一致する必要があります。  たとえば、日付として設定されているデータセット列で日付時刻値や数値を検索する場合、"文字列" 型のテーブル列を指定しても動作しません (例: Table/StringColumn eq 1)。

* **文字列**は単一引用符で囲む必要があります (例: 'manager name')。
* **数値**には特別な書式設定は必要ありません。
* **日付と時刻**は単一引用符で囲み、前に **DateTime** という単語を付ける必要があります。

以下では構文についてさらに詳しく説明します。  

## <a name="filter-on-a-field"></a>フィールドをフィルター処理する

次のようなレポートの URL があるものとします。

![URL の開始](media/service-url-filters/power-bi-filter-urls6.png)

そして、ノースカロライナ州の店舗に関するマップの視覚化 (上図) を表示します。

>[!NOTE]
>この例は、[Retail Analysis サンプル](sample-datasets.md)が基になっています。
> 

"NC" (ノースカロライナ) の店舗のデータだけが表示されるようにレポートをフィルター処理するには、URL に以下を追加します。

?filter=Store/Territory eq 'NC'

![フィルターを含む URL](media/service-url-filters/power-bi-filter-urls7.png)

>[!NOTE]
>*NC* は、**Store** テーブルの **Territory** フィールドに格納されている値です。
> 

レポートはノースカロライナでフィルター処理されます。レポート ページのすべての視覚化には、ノースカロライナのデータだけが表示されます。

![](media/service-url-filters/power-bi-report4.png)

## <a name="filter-on-multiple-fields"></a>複数のフィールドでフィルター処理する

URL にパラメーターを追加し、複数のフィールドでフィルター処理することもできます。 元のフィルター パラメーターに戻りましょう。

```
?filter=Store/Territory eq 'NC'
```

追加フィールドでフィルター処理するには、上記と同じ形式で **and** と別のフィールドを追加します。 次に例を示します。

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

<iframe width="640" height="360" src="https://www.youtube.com/embed/0sDGKxOaC8w?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="operators"></a>演算子

Power BI では、**and** に加え、多くの演算子がサポートされます。 次の表に、その演算子とサポートされるコンテンツの種類を一覧表示します。

|演算子  | 定義 | 文字列  | 数値 | 日付 |  例|
|---------|---------|---------|---------|---------|---------|
|**and**     | AND |  はい      | はい |  はい|  product/price le 200 and price gt 3.5 |
|**eq**     | 指定の値に等しい |  はい      | はい   |  はい       | Address/City eq 'Redmond' |
|**ne**     | 等しくない |   はい      | はい  | はい        |  Address/City ne 'London' |
|**ge**     |  以上       | いいえ | はい |はい |  product/price ge 10
|**gt**     | より大きい        |いいえ | はい | はい  | product/price gt 20
|**le**     |   以下      | いいえ | はい | はい  | product/price le 100
|**lt**     |  より小さい       | いいえ | はい | はい |  product/price lt 20
|**in****     |  含む       | いいえ | いいえ |  はい | Student/Age in (27, 29)


\** **in** を使用する場合、**in** の右側の値をかっこで囲んだコンマ区切りのリストにすることができます。あるいは、コレクションを返す単一の式にすることもできます。

### <a name="numeric-data-types"></a>数値データ型

Power BI の URL フィルターには、次の形式で数値を含めることができます。

|数値型  |例  |
|---------|---------|
|**integer**     |   5      |
|**long**     |   5L、5l      |
|**double**     |   5.5、55e-1、0.55e+1、5D、5d、0.5e1D、0.5e1d、5.5D、5.5d、55e-1D、55e-1d     |
|**decimal**     |   5M、5m、5.5M、5.5m      |
|**float**     | 5F、5f、0.5e1F、0.5e-1d        |

### <a name="date-data-types"></a>日付データ型

Power BI では、**Date** および **DateTimeOffset** データ型で OData V3 と V4 の両方がサポートされます。  日付は EDM 形式を使用して表されます (2019-02-12T00:00:00)。 つまり、日付を YYYY-MM-DD として指定した場合、Power BI では YYYY-MM-DDT00:00:00 と解釈されます。

この区別が重要なのはなぜでしょうか?  たとえば、**Table/Date gt 2018-08-03** というクエリ文字列パラメーターを作成するとします。  結果には August 3rd 2018 が含まれるのでしょうか? あるいは August 4th 2018 で始まるのでしょうか?  Power BI ではクエリが **Table/Date gt 2018-08-03T00:00:00** に変換されるため、ゼロ以外の時刻部分を含む日付が結果に含まれます。これは、日付が **2018-08-03T00:00:00** より大きいためです。

## <a name="special-characters-in-url-filters"></a>URL フィルター内の特殊文字

特殊文字とスペースにはいくつか追加の書式設定が必要です。 クエリにスペース、ダッシュ、またはその他の非 ASCII 文字が含まれている場合は、それらの特殊文字の前に*エスケープ コード* (**_x**) と 4 桁の **Unicode** を付けます。 Unicode が 4 文字未満の場合は、ゼロで埋める必要があります。 次に例をいくつか示します。

|識別子  |Unicode  | Power BI 用のコーディング  |
|---------|---------|---------|
|**テーブル名**     | スペース: 0x20        |  Table_x0020_Name       |
|**列**@**数値**     |   @: 0x40     |  Column_x0040_Number       |
|**[列]**     |  [:0x005B ]:0x0050       |  _x0058_Column_x0050       |
|**列+プラス**     | +:0x2B        |  Column_x002B_Plus       |

Table_x0020_Name/Column_x002B_Plus eq 3 ![ 特殊文字をレンダリングするテーブルのビジュアル](media/service-url-filters/power-bi-special-characters1.png)


Table_x0020_Special/_x005B_Column_x0020_Brackets_x005D_ eq '[C]' ![特殊文字をレンダリングするテーブルのビジュアル](media/service-url-filters/power-bi-special-characters2.png)

### <a name="use-dax-to-filter-on-multiple-values"></a>DAX を使用して複数の値をフィルター処理する

複数のフィールドにフィルターを適用するもう 1 つの方法は、2 つのフィールドを 1 つの値に連結する計算列を作成することです。 その後は、その値に対してフィルターを適用できます。

たとえば、この例には Territory と Chain という 2 つのフィールドがあります。 Power BI Desktop で、TerritoryChain という名前の[新しい計算列 (フィールド) を作成](desktop-tutorial-create-calculated-columns.md)します。 **フィールド**名にスペースが含まれてはならないことに注意してください。 その列に DAX 式は次のようになります。

TerritoryChain = [Territory] & " - " & [Chain]

レポートを Power BI サービスに公開した後、URL クエリ文字列を使って、NC の Lindseys 店のデータだけを表示するようにフィルター処理します。

    https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Store/TerritoryChain eq 'NC–Lindseys'

## <a name="pin-a-tile-from-a-filtered-report"></a>フィルター処理されたレポートのタイルをピン留めする

クエリ文字列パラメーターを使ってレポートをフィルター処理した後は、そのレポートの視覚化をダッシュボードにピン留めできます。  ダッシュボードのタイルにはフィルター処理されたデータが表示され、そのダッシュボードのタイルを選ぶと、タイルの作成に使われたレポートが表示されます。  ただし、URL を使って行ったフィルター処理はレポートと共には保存されず、ダッシュボードのタイルを選ぶと、フィルター処理されていない状態のレポートが開きます。  つまり、ダッシュボードのタイルに表示されたデータは、レポートの視覚化に表示されるデータと一致しません。

これは、フィルター処理されたダッシュボードとフィルター処理されていないレポートで、異なる結果を見たい場合に役立ちます。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

クエリ文字列パラメーターを使う場合に注意すべき点が 2 つあります。

* *in* 演算子を使用する場合は、*in* の右側の値をかっこで囲んだコンマ区切りのリストにする必要があります。    
* Power BI Report Server で、レポートの URL に含ませることによって[レポート パラメーターを渡す](https://docs.microsoft.com/sql/reporting-services/pass-a-report-parameter-within-a-url?view=sql-server-2017.md)ことができます。 レポート処理エンジンに直接渡されるため、これらの URL パラメーターにはプレフィックスが付いていません。
* クエリ文字列のフィルター処理は、[[Web に公開]](service-publish-to-web.md) または Power BI Embedded では機能しません。   
* JavaScript の制限により、long データ型は (2^53-1) となります。

## <a name="next-steps"></a>次の手順

[視覚化をダッシュボードにピン留めする](service-dashboard-pin-tile-from-report.md)  
[無料試用版にサインアップ](https://powerbi.microsoft.com/get-started/)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](http://community.powerbi.com/)。
