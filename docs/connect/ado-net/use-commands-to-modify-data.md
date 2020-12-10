---
title: Verwenden von Befehlen zum Ändern von Daten
description: Beschreibt die Verwendung eines Datenanbieters zum Ausführen gespeicherter Prozeduren oder von DDL-Anweisungen (Data Definition Language).
ms.date: 11/25/2020
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 98127e41b5b07c38030ef27214c9c92bf7c4b4be
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761478"
---
# <a name="using-commands-to-modify-data"></a>Verwenden von Befehlen zum Ändern von Daten

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Mithilfe des Microsoft SqlClient-Datenanbieters für SQL Server können Sie gespeicherte Prozeduren oder DDL-Anweisungen (z. B. CREATE TABLE und ALTER COLUMN) ausführen, um das Schema einer Datenbank oder eines Katalogs zu bearbeiten. Bei diesen Befehlen werden keine Zeilen zurückgegeben, wie es bei einer Abfrage der Fall wäre. Daher stellt das <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekt eine <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>-Methode für die Verarbeitung bereit.

Mit der **ExecuteNonQuery**-Methode können Sie sowohl ein Schema ändern als auch SQL-Anweisungen verarbeiten, die Daten ändern, aber keine Zeilen zurückgeben, z. B. INSERT, UPDATE und DELETE.

Obwohl von der **ExecuteNonQuery**-Methode keine Zeilen zurückgegeben werden, können Eingabeparameter, Ausgabeparameter und Rückgabewerte übergeben und über die **Parameters**-Auflistung des **Command**-Objekts zurückgegeben werden.

## <a name="in-this-section"></a>In diesem Abschnitt

[Aktualisieren von Daten in einer Datenquelle](update-data-inside-data-source.md)  
Beschreibt das Ausführen von Befehlen oder gespeicherten Prozeduren, mit denen Daten in einer Datenbank geändert werden.

[Ausführen von Katalogoperationen](perform-catalog-operations.md)  
Beschreibt das Ausführen von Befehlen, mit denen ein Datenbankschema geändert wird.

## <a name="see-also"></a>Weitere Informationen:

- [Abrufen und Ändern von Daten in ADO.NET](retrieving-modifying-data.md)
- [Befehle und Parameter](commands-parameters.md)
- [Microsoft ADO.NET für SQL Server](microsoft-ado-net-sql-server.md)
