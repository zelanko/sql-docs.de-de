---
title: Unterschlüssel ODBC-Datenquellen | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c5e97e643a78187b15e91833c832cd16ca435c7f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304057"
---
# <a name="odbc-data-sources-subkey"></a>ODBC-Datenquellen-Unterschlüssel

Die Werte `ODBC Data Sources` unter dem Unterschlüssel listen die Datenquellen auf. Das Format dieser Werte wird in der folgenden Tabelle angezeigt.

| Name | Datentyp | Daten |
| :--- | :-------- | :--- |
| *Datenquellenname* | REG_SZ | *Treiberbeschreibung* |
| &nbsp; | &nbsp; | &nbsp; |

Der Wert des *Datenquellennamens* wird vom Administrationsprogramm definiert (was den Benutzer normalerweise dazu auffordert), und die *Treiberbeschreibung* wird vom Treiberentwickler definiert (in der Regel ist dies der Name des DBMS, der dem Treiber zugeordnet ist).

Angenommen, es wurden drei Datenquellen definiert: Inventur, die SQL Server verwendet; Lohnabrechnung, die dBASE verwendet; und Personal, das formatierte Textdateien verwendet. Die Werte `ODBC Data Sources` unter dem Unterschlüssel können wie folgt lauten:

```console
Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text
```
