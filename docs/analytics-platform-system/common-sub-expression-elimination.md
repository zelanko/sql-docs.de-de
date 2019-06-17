---
title: Allgemeine Teilausdruck erläutert in Analytics Platform System | Microsoft-Dokumentation
description: Zeigt Beispiel Abfrage Verbesserung, die in Analytics Platform System CU7.3 eingeführt wurde
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 12/17/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: 2dd02bed55f3d3781428eae3ec4bc2d0655819ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63312470"
---
# <a name="common-subexpression-elimination-explained"></a>Allgemeine teilausdruckbeseitigung erläutert

APS-CU7.3 verbessert die abfrageleistung mit gängiger Unterausdrücke in SQL-Abfrageoptimierer. Die Verbesserung der verbessert die Abfragen auf zwei Arten. Der erste Vorteil ist die Möglichkeit, erkennen und zu eliminieren, z. B. Ausdrücken können SQL-Kompilierungszeit zu reduzieren. Der zweite, wichtigere-Vorteil ist, dass Verschiebevorgänge für Abfragedaten für diesen redundanten Teilausdrücken daher Ausführungszeit behoben wurden, für Abfragen wird schneller.

```sql
select top 100 asceding.rnk, i1.i_product_name best_performing, i2.i_product_name worst_performing
  from(select *
       from (select item_sk,rank() over (order by rank_col asc) rnk
             from (select ss_item_sk item_sk,avg(ss_net_profit) rank_col
                   from store_sales ss1
                   where ss_store_sk = 8
                   group by ss_item_sk
                   having avg(ss_net_profit) > 0.9*(select avg(ss_net_profit) rank_col
                                                    from store_sales
                                                    where ss_store_sk = 8
                                                      and ss_hdemo_sk is null
                                                    group by ss_store_sk))V1)V11
       where rnk  < 11) asceding,
      (select *
       from (select item_sk,rank() over (order by rank_col desc) rnk
             from (select ss_item_sk item_sk,avg(ss_net_profit) rank_col
                   from store_sales ss1
                   where ss_store_sk = 8
                   group by ss_item_sk
                   having avg(ss_net_profit) > 0.9*(select avg(ss_net_profit) rank_col
                                                    from store_sales
                                                    where ss_store_sk = 8
                                                      and ss_hdemo_sk is null
                                                    group by ss_store_sk))V2)V21
       where rnk  < 11) descending,
  item i1,
  item i2
  where asceding.rnk = descending.rnk
    and i1.i_item_sk=asceding.item_sk
    and i2.i_item_sk=descending.item_sk
  order by asceding.rnk
  ;
```
Erwägen Sie die obige Abfrage TPC-DS-Benchmark-Tools.  Klicken Sie in der obigen Abfrage wird die Unterabfrage ist identisch, aber die Order by-Klausel mit rank() über Funktion auf zwei unterschiedliche Arten sortiert wird. Vor CU7.3 diese Unterabfrage bewertet und zweimal ausgeführt, nachdem für aufsteigender Reihenfolge und einmal für eine absteigende Reihenfolge an, dass zwei datenverschiebungsvorgänge. Nach der Installation der APS-CU7.3, wird das Teil der Unterabfrage ausgewertet einmal daher reduzieren die datenverschiebung und die Abfrage schneller abgeschlossen.

Wir eingeführt haben eine [featureschalter](appliance-feature-switch.md) "OptimizeCommonSubExpressions" aufgerufen wird, können Sie die Funktion testen, selbst nach einem upgrade auf APS CU7.3. Das Feature ist standardmäßig aktiviert und kann deaktiviert werden. 

> [!NOTE] 
> Änderungen an Werten für Feature-Switch erfordert einen Neustart des Diensts.

Sie können die Beispielabfrage versuchen, durch den folgenden Tabellen in Ihrer testumgebung erstellen und Auswerten der Explain Plans für die oben genannten Abfrage. 

```sql
CREATE TABLE [dbo].[store_sales] (
    [ss_sold_date_sk] int NULL, 
    [ss_sold_time_sk] int NULL, 
    [ss_item_sk] int NOT NULL, 
    [ss_customer_sk] int NULL, 
    [ss_cdemo_sk] int NULL, 
    [ss_hdemo_sk] int NULL, 
    [ss_addr_sk] int NULL, 
    [ss_store_sk] int NULL, 
    [ss_promo_sk] int NULL, 
    [ss_ticket_number] int NOT NULL, 
    [ss_quantity] int NULL, 
    [ss_wholesale_cost] decimal(7, 2) NULL, 
    [ss_list_price] decimal(7, 2) NULL, 
    [ss_sales_price] decimal(7, 2) NULL, 
    [ss_ext_discount_amt] decimal(7, 2) NULL, 
    [ss_ext_sales_price] decimal(7, 2) NULL, 
    [ss_ext_wholesale_cost] decimal(7, 2) NULL, 
    [ss_ext_list_price] decimal(7, 2) NULL, 
    [ss_ext_tax] decimal(7, 2) NULL, 
    [ss_coupon_amt] decimal(7, 2) NULL, 
    [ss_net_paid] decimal(7, 2) NULL, 
    [ss_net_paid_inc_tax] decimal(7, 2) NULL, 
    [ss_net_profit] decimal(7, 2) NULL
)
WITH (CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH([ss_item_sk]),  PARTITION ([ss_sold_date_sk] RANGE RIGHT FOR VALUES (2450815, 2451180, 2451545, 2451911, 2452276, 2452641, 2453006)));

CREATE TABLE [dbo].[item] (
    [i_item_sk] int NOT NULL, 
    [i_item_id] char(16) COLLATE Latin1_General_100_CI_AS_KS_WS NOT NULL, 
    [i_rec_start_date] date NULL, 
    [i_rec_end_date] date NULL, 
    [i_item_desc] varchar(200) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_current_price] decimal(7, 2) NULL, 
    [i_wholesale_cost] decimal(7, 2) NULL, 
    [i_brand_id] int NULL, 
    [i_brand] char(50) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_class_id] int NULL, 
    [i_class] char(50) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_category_id] int NULL, 
    [i_category] char(50) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_manufact_id] int NULL, 
    [i_manufact] char(50) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_size] char(20) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_formulation] char(20) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_color] char(20) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_units] char(10) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_container] char(10) COLLATE Latin1_General_100_CI_AS_KS_WS NULL, 
    [i_manager_id] int NULL, 
    [i_product_name] char(50) COLLATE Latin1_General_100_CI_AS_KS_WS NULL
)
WITH (CLUSTERED INDEX ( [i_item_sk] ASC ), DISTRIBUTION = REPLICATE);
```
Wenn Sie sehen Sie sich die Explain Plans der Abfrage, Sie, dass vor dem CU7.3 sehen (oder wenn der featureschalter deaktiviert ist) wird die Abfrage enthält 17 Gesamtanzahl von Vorgängen und nach CU7.3 (oder mit der featureschalter aktiviert) die gleiche Abfrage zeigt 9 Gesamtanzahl von Vorgängen. Wenn Sie nur die datenverschiebungsvorgänge zählen, sehen Sie sich, dass es sich bei der vorherige Plan vier Move-Vorgänge im Vergleich zu zwei Move-Vorgänge in den neuen Plan verfügt. Die neue Abfrageoptimierer konnte zwei datenverschiebungsvorgänge reduzieren, indem Sie die temporäre Tabelle, die sie bereits erstellt haben, mit der neue Plan, wodurch die abfragelaufzeit wiederverwenden. 


