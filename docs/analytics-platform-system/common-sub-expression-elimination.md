---
title: Gemeinsamer Teil Ausdruck
description: Zeigt eine Beispiel Abfrage Verbesserung an, die in Analytics Platform System Cu 7.3 eingeführt wurde.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 12/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
monikerRange: '>= aps-pdw-2016-au7'
ms.openlocfilehash: 8dfadabcae27ff8705d86294b1c05851245d199c
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97420199"
---
# <a name="common-subexpression-elimination-explained"></a>Erläuterung der allgemeinen Teil Ausdrucks Löschung

APS Cu 7.3 verbessert die Abfrageleistung mit allgemeiner Teil Ausdrucks Löschung im SQL-Abfrageoptimierer. Die Verbesserung verbessert Abfragen auf zwei Arten. Der erste Vorteil ist die Möglichkeit, solche Ausdrücke zu identifizieren und zu entfernen, um die SQL-Kompilierungszeit zu verringern. Der zweite und wichtigere Vorteil besteht darin, dass Daten Verschiebungs Vorgänge für diese redundanten Teil Ausdrücke eliminiert werden, sodass die Ausführungszeit für Abfragen schneller wird.

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
Sehen Sie sich die obige Abfrage von TPC-DS-Benchmark-Tools an.  In der obigen Abfrage ist die Unterabfrage identisch, aber die Order By-Klausel mit der Rang () over-Funktion ist auf zwei verschiedene Arten sortiert. Vor Cu 7.3 wird diese Unterabfrage zweimal ausgewertet und ausgeführt, einmal in aufsteigender Reihenfolge und einmal für absteigende Reihenfolge, sodass zwei Daten Verschiebungs Vorgänge durchgeführt werden. Nach der Installation von APS Cu 7.3 wird der Teil Abfrage Teil ausgewertet, um die Daten Verschiebung zu verringern und die Abfrage schneller abzuschließen.

Wir haben einen [Funktions Schalter](appliance-feature-switch.md) mit dem Namen "optimizecommonsubexausdrucks" eingeführt, mit dem Sie das Feature auch nach dem Upgrade auf APS Cu 7.3 testen können. Die Funktion ist standardmäßig aktiviert, kann aber deaktiviert werden. 

> [!NOTE] 
> Änderungen an Funktions switchwerten erfordern einen Neustart des Dienstanbieter.

Sie können die Beispiel Abfrage ausprobieren, indem Sie die folgenden Tabellen in der Testumgebung erstellen und den Erläuterungs Plan für die oben genannte Abfrage auswerten. 

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
Wenn Sie sich den Erläuterungs Plan der Abfrage ansehen, werden Sie feststellen, dass die Abfrage vor Cu 7.3 (oder wenn der Funktions Schalter deaktiviert ist) 17 Gesamtanzahl von Vorgängen und nach Cu 7.3 (oder mit aktiviertem Funktions Wechsel) eine Gesamtanzahl von Vorgängen anzeigt. Wenn Sie nur die Daten Verschiebungs Vorgänge zählen, sehen Sie, dass der vorherige Plan vier Verschiebe Vorgänge im Vergleich zu zwei Verschiebungs Vorgängen im neuen Plan umfasst. Der neue Abfrageoptimierer konnte zwei Daten Verschiebungs Vorgänge verringern, indem er die temporäre Tabelle wieder verwendet, die bereits mit dem neuen Plan erstellt wurde, wodurch die Abfrage Laufzeit verringert wird. 


