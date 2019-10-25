---
title: Binäre Daten und Daten mit umfangreichen Werten in SQL Server
description: Beschreibt das Arbeiten mit Daten mit umfangreichen Werten in SQL Server.
ms.date: 08/15/2019
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 0a38d90a810f9ca3ee376562eaabf6e713267b27
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452050"
---
# <a name="sql-server-binary-and-large-value-data"></a>Binäre Daten und Daten mit umfangreichen Werten in SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server stellt den `max` Spezifizierer bereit, der die Speicherkapazität der Datentypen `varchar`, `nvarchar` und `varbinary` erweitert. `varchar(max)`, `nvarchar(max)` und `varbinary(max)` werden zusammenfassend als *Datentypen mit umfangreichen Werten* bezeichnet. Sie können die Datentypen mit umfangreichen Werten zum Speichern von bis zu 2^31-1 Bytes an Daten verwenden.  
  
In SQL Server 2008 wird das FILESTREAM-Attribut eingeführt, bei dem es sich nicht um einen-Datentyp handelt, sondern um ein Attribut, das für eine Spalte definiert werden kann, sodass Daten mit umfangreichen Werten im Dateisystem und nicht in der Datenbank gespeichert werden können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Ändern von Daten mit umfangreichen Werten (max) in ADO.NET](modify-large-value-max-data.md)  
Beschreibt das Arbeiten mit Datentypen mit umfangreichen Werten.  
  
[FILESTREAM-Daten](filestream-data.md)  
Beschreibt das Arbeiten mit Daten mit umfangreichen Werten, die in SQL Server 2008 mit dem FILESTREAM-Attribut gespeichert sind.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Datentypen und ADO.NET](sql-server-data-types.md)
- [SQL Server-Datenvorgänge in ADO.NET](sql-server-data-operations.md)
