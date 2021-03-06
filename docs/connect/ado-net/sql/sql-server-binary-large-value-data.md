---
title: Binäre Daten und Daten mit umfangreichen Werten in SQL Server
description: Beschreibt das Arbeiten mit Daten mit umfangreichen Werten in SQL Server.
ms.date: 08/15/2019
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 17a38bd45a467625be467f5fb01f0e733f7546bc
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920972"
---
# <a name="sql-server-binary-and-large-value-data"></a>Binäre Daten und Daten mit umfangreichen Werten in SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server stellt den `max`-Spezifizierer bereit, der die Speicherkapazität der Datentypen `varchar`, `nvarchar` und `varbinary` erweitert. `varchar(max)`, `nvarchar(max)` und `varbinary(max)` werden zusammenfassend als *Datentypen mit umfangreichen Werten* bezeichnet. Sie können die Datentypen mit umfangreichen Werten zum Speichern von bis zu 2^31-1 Bytes an Daten verwenden.  
  
In SQL Server 2008 wurde das FILESTREAM-Attribut eingeführt, das kein Datentyp ist. Es ist ein Attribut, das für eine Spalte definiert werden kann, wodurch Daten mit umfangreichen Werten im Dateisystem anstatt in der Datenbank gespeichert werden können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Ändern von Daten mit umfangreichen Werten (max) in ADO.NET](modify-large-value-max-data.md)  
Beschreibt das Arbeiten mit den Datentypen für große Werte.  
  
[FILESTREAM-Daten](filestream-data.md)  
Beschreibt, wie Sie mit Daten mit großen Werten arbeiten, die in SQL Server 2008 mit dem FILESTREAM-Attribut gespeichert sind.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Datentypen und ADO.NET](sql-server-data-types.md)
- [SQL Server-Datenvorgänge in ADO.NET](sql-server-data-operations.md)
