---
title: Ausführen von Katalogoperationen
description: Beschreibt das Ausführen von Befehlen, mit denen ein Datenbankschema geändert wird.
ms.date: 11/25/2020
dev_langs:
- csharp
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 85e68bd77b11fd70e4071d7ae67ebf26c643b540
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96428244"
---
# <a name="performing-catalog-operations"></a>Ausführen von Katalogoperationen

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Um einen Befehl zum Ändern einer Datenbank oder eines Katalogs (z. B. die CREATE TABLE- oder die CREATE PROCEDURE-Anweisung) auszuführen, erstellen Sie ein **Command**-Objekt mithilfe der entsprechenden SQL-Anweisungen und eines **Connection**-Objekts. Führen Sie den Befehl mit der <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>-Methode des <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekts aus.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird eine gespeicherte Prozedur in einer Microsoft SQL Server-Datenbank erstellt.

[!code-csharp[DataWorks SqlCommand.ExecuteNonQuery#3](~/../sqlclient/doc/samples/SqlCommand_ExecuteNonQuery_SP_DML.cs#3)]

## <a name="see-also"></a>Weitere Informationen:

- [Verwenden von Befehlen zum Ändern von Daten](use-commands-to-modify-data.md)
- [Befehle und Parameter](commands-parameters.md)
