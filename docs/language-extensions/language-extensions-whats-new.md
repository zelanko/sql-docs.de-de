---
title: Neuerungen bei SQL Server-Spracherweiterungen
titleSuffix: ''
description: Erfahren Sie mehr über die Neuerungen in SQL Server-Spracherweiterungen, mit denen die Integration zwischen externen Sprachen und der Datenplattform ausgebaut, erweitert und vertieft wird.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4a38bba48d9accd16a3e8ca68bd3136c3419e5ad
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88173513"
---
# <a name="whats-new-in-sql-server-language-extensions"></a>Neuerungen bei SQL Server-Spracherweiterungen
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

SQL Server werden in jedem Release Funktionen für [Spracherweiterungen](language-extensions-overview.md) hinzugefügt, während wir die Integration zwischen externen Sprachen und der Datenplattform kontinuierlich ausbauen, erweitern und vertiefen. 

## <a name="new-in-sql-server-2019"></a>Neues in SQL Server 2019 

In diesem Release wird Unterstützung für Spracherweiterungen in SQL Server hinzugefügt. Weitere Informationen zu allen Features in diesem Release finden Sie unter [Neuerungen in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md) und [Versionshinweise für SQL Server 2019](../sql-server/sql-server-ver15-release-notes.md).

- Die Standard-Java-Runtime unter Windows und Linux heißt Open Zulu JRE und ist in der [Installation von SQL Server-Spracherweiterungen unter Windows](install/install-sql-server-language-extensions-on-windows.md) und der [Installation von SQL Server-Spracherweiterungen unter Linux](../linux/sql-server-linux-setup-language-extensions.md) enthalten.
- Unterstützte [Java-Datentypen](how-to/java-to-sql-data-types.md).
- [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md) zum Registrieren einer externen Sprache (z. B. Java) in SQL Server.
- [Microsoft-Erweiterbarkeits-SDK für Java](how-to/extensibility-sdk-java-sql-server.md).
- Unter Windows und Linux kann mithilfe der Anweisung [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) über eine externe Bibliothek auf Java-Code zugegriffen werden. Weitere Informationen: [Aufrufen von Java aus SQL Server](how-to/call-java-from-sql.md).
- [Java-Spracherweiterung](language-extensions-overview.md) unter Windows und Linux. Sie können kompilierten Java-Code für SQL Server zur Verfügung stellen, indem Sie Berechtigungen zuweisen und den Pfad festlegen. Client-Apps mit Zugriff auf SQL Server können Daten verwenden und durch Aufrufen von [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) Ihren Code ausführen. Dies ist dasselbe Verfahren, das auch für die R- und Python-Integration in SQL Server Machine Learning Services verwendet wird.

## <a name="next-steps"></a>Nächste Schritte

+ Installieren von [SQL Server-Spracherweiterungen unter Windows](install/install-sql-server-language-extensions-on-windows.md) oder [unter Linux](../linux/sql-server-linux-setup-language-extensions.md)
