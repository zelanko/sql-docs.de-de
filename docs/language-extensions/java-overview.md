---
title: Was ist die Java-Spracherweiterung?
titleSuffix: SQL Server Language Extensions
description: Die Java-Spracherweiterung ist ein Feature von SQL Server, das zum Ausführen von externem Java-Code dient. Relationale Daten können über das Erweiterbarkeitsframework im externen Java-Code verwendet werden.
author: dphansen
ms.author: davidph
ms.date: 11/10/2020
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15'
ms.openlocfilehash: f68821900b2e304028bccfd79e96f988f02267e9
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471721"
---
# <a name="what-is-java-language-extension"></a>Was ist die Java-Spracherweiterung?
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Die Java-Spracherweiterung ist ein Feature von SQL Server, das zum Ausführen von externem Java-Code dient. Die relationalen Daten können über das [Erweiterbarkeitsframework](concepts/extensibility-framework.md) im externen Java-Code verwendet werden. Die Java-Spracherweiterung gehört zu den [SQL Server-Spracherweiterungen](language-extensions-overview.md).

Die Java-Standardruntime ist Zulu Open JRE. Sie können auch eine andere Java-JRE oder ein anderes SDK verwenden.

## <a name="what-you-can-do-with-the-java-language-extension"></a>Zwecke der Java-Spracherweiterung

Die Java-Spracherweiterung nutzt das Erweiterbarkeitsframework zum Ausführen von externem Java-Code. Die Codeausführung ist von den Prozessen der Kern-Engine isoliert, aber vollständig in die Ausführung von SQL Server-Abfragen integriert. Sie können Java-Code an der Quelle der Daten ausführen und so die Notwendigkeit umgehen, Daten über das Netzwerk abzurufen.

Die externe Sprache Java wird mit [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql) definiert. Die gespeicherte Systemprozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) dient als Schnittstelle für die Ausführung des Java-Codes.

## <a name="get-started-with-java-language-extension"></a>Erste Schritte mit der Java-Spracherweiterung

1. [Installieren Sie die Java-Spracherweiterung für SQL Server unter Windows](install/windows-java.md) oder [Linux](../linux/sql-server-linux-setup-language-extensions-java.md).

1. Konfigurieren Sie Entwicklungstools.

    + Verwenden Sie Ihre bevorzugte IDE zum Entwickeln von Java-Code.
    + Installieren Sie das [Microsoft-Erweiterbarkeits-SDK](how-to/extensibility-sdk-java-sql-server.md) für Java, um Java-Code in SQL Server auszuführen.
    + Führen Sie externen Code mithilfe von [Azure Data Studio](../azure-data-studio/what-is.md) in SQL Server aus.
    + Verwenden Sie die gespeicherte Systemprozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql), um Ihren Java-Code in SQL Server auszuführen.

1. Schreiben Sie Ihren ersten Java-Code.

    + [Tutorial: Reguläre Ausdrücke in Java](tutorials/search-for-string-using-regular-expressions-in-java.md)

## <a name="limitations"></a>Einschränkungen

Die Anzahl von Werten in den Ein- und Ausgabepuffern darf `MAX_INT (2^31-1)` nicht überschreiten, da dies die maximale Anzahl von Elementen ist, die einem Array in Java zugeordnet werden können.

## <a name="next-steps"></a>Nächste Schritte

+ Installieren der [Java-Spracherweiterung für SQL Server](install/windows-java.md) unter Windows oder [Linux](../linux/sql-server-linux-setup-language-extensions-java.md)
+ Installieren Sie des [Microsoft-Erweiterbarkeits-SDKs für Java](how-to/extensibility-sdk-java-sql-server.md)
