---
title: Unterschlüssel für ODBC-Datenquellen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4d6d54d1fc7c7742bf94e91d7370f356e28b5624
ms.sourcegitcommit: 816ff47eeab157c66e0f75f18897a63dc8033502
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71207689"
---
# <a name="odbc-data-sources-subkey"></a>Unterschlüssel für ODBC-Datenquellen

Die Werte unter dem `ODBC Data Sources` Unterschlüssel Listen die Datenquellen auf. Das Format dieser Werte wird in der folgenden Tabelle dargestellt.

| Name | Datentyp | Daten |
| :--- | :-------- | :--- |
| *data-source-name* | REG_SZ | *Treiber Beschreibung* |
| &nbsp; | &nbsp; | &nbsp; |

Der Wert für *Datenquellen Name* wird vom Verwaltungs Programm definiert (das normalerweise den Benutzer dazu auffordert), und die *Treiber Beschreibung* wird vom Treiber Entwickler definiert (in der Regel ist dies der Name des DBMS, das dem Treiber zugeordnet ist).

Nehmen wir beispielsweise an, dass drei Datenquellen definiert wurden: Inventur, die SQL Server verwendet; Gehaltsliste, die dBASE verwendet; und Mitarbeiter, die formatierte Textdateien verwenden. Die Werte unter dem `ODBC Data Sources` Unterschlüssel können wie folgt lauten:

```console
Inventory : REG_SZ : SQL Server
Payroll : REG_SZ : dBASE
Personnel : REG_SZ : Text
```
