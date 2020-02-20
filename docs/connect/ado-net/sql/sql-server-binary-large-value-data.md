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
ms.openlocfilehash: e60f8ce6bc8e7ef05a2de942d8bbc2885095d493
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251123"
---
# <a name="sql-server-binary-and-large-value-data"></a>Binäre Daten und Daten mit umfangreichen Werten in SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

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
