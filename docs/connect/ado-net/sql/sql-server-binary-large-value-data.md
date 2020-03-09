---
title: Binäre Daten und Daten mit umfangreichen Werten in SQL Server
description: Beschreibt das Arbeiten mit Daten mit umfangreichen Werten in SQL Server.
ms.date: 08/15/2019
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 4ed8ccbadb27008fb15d9d117d55b5a4d332a8f6
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896631"
---
# <a name="sql-server-binary-and-large-value-data"></a>Binäre Daten und Daten mit umfangreichen Werten in SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server stellt den `max`-Spezifizierer bereit, der die Speicherkapazität der Datentypen `varchar`, `nvarchar` und `varbinary` erweitert. `varchar(max)`, `nvarchar(max)` und `varbinary(max)` werden zusammenfassend als *Datentypen mit umfangreichen Werten* bezeichnet. Sie können die Datentypen mit umfangreichen Werten zum Speichern von bis zu 2^31-1 Bytes an Daten verwenden.  
  
In SQL Server 2008 wurde das FILESTREAM-Attribut eingeführt, das kein Datentyp ist. Es ist ein Attribut, das für eine Spalte definiert werden kann, wodurch Daten mit umfangreichen Werten im Dateisystem anstatt in der Datenbank gespeichert werden können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Ändern von Daten mit umfangreichen Werten (max) in ADO.NET](modify-large-value-max-data.md)  
Beschreibt die Verwendung von Datentypen mit umfangreichen Werten  
  
[FILESTREAM-Daten](filestream-data.md)  
Beschreibt die Verwendung von Daten mit umfangreichen Werten, die mit dem FILESTREAM-Attribut in SQL Server 2008 gespeichert wurden  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Datentypen und ADO.NET](sql-server-data-types.md)
- [SQL Server-Datenvorgänge in ADO.NET](sql-server-data-operations.md)
