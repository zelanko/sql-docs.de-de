---
title: Neuerungen bei SQL Server-Spracherweiterungen
titleSuffix: ''
description: Erfahren Sie mehr über die Neuerungen in SQL Server-Spracherweiterungen, mit denen die Integration zwischen externen Sprachen und der Datenplattform ausgebaut, erweitert und vertieft wird.
author: dphansen
ms.author: davidph
ms.date: 11/09/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15'
ms.openlocfilehash: b737f8764f387faa88d0e5de0c844e55c89a4a30
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471701"
---
# <a name="whats-new-in-sql-server-language-extensions"></a>Neuerungen bei SQL Server-Spracherweiterungen
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

SQL Server werden in jedem Release Funktionen für [Spracherweiterungen](language-extensions-overview.md) hinzugefügt, während wir die Integration zwischen externen Sprachen und der Datenplattform kontinuierlich ausbauen, erweitern und vertiefen.

## <a name="sql-server-2019"></a>SQL Server 2019

Informationen zu den neuen Möglichkeiten von [Spracherweiterungen](language-extensions-overview.md) in SQL Server 2019 finden Sie nachstehend. Weitere Informationen zu allen Features in diesem Release finden Sie unter [Neuerungen in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md) und [Versionshinweise für SQL Server 2019](../sql-server/sql-server-version-15-release-notes.md).

### <a name="new-python-and-r-language-extensions"></a>Neue Spracherweiterungen für Python und R

- Über Spracherweiterungen steht eine [benutzerdefinierte Python-Runtime](../machine-learning/install/custom-runtime-python.md) zur Verfügung. Weitere Informationen finden Sie unter [Installieren einer benutzerdefinierten Python-Runtime unter Windows](../machine-learning/install/custom-runtime-python.md?view=sql-server-ver15&preserve-view=true) oder [Installieren einer benutzerdefinierten Python-Runtime unter Linux](../machine-learning/install/custom-runtime-python.md?view=sql-server-linux-ver15&preserve-view=true).

- Über Spracherweiterungen steht eine [benutzerdefinierte R-Runtime](../machine-learning/install/custom-runtime-r.md) zur Verfügung. Weitere Informationen finden Sie unter [Installieren einer benutzerdefinierten R-Runtime unter Windows](../machine-learning/install/custom-runtime-r.md?view=sql-server-ver15&preserve-view=true) oder [Installieren einer benutzerdefinierten R-Runtime unter Linux](../machine-learning/install/custom-runtime-r.md?view=sql-server-linux-ver15&preserve-view=true).

### <a name="new-java-language-extension"></a>Neue Java-Spracherweiterung

- Die Standard-Java-Runtime unter Windows und Linux heißt Open Zulu JRE und ist in der [Installation von SQL Server-Spracherweiterungen unter Windows](install/windows-java.md) und der [Installation von SQL Server-Spracherweiterungen unter Linux](../linux/sql-server-linux-setup-language-extensions-java.md) enthalten.
- Unterstützte [Java-Datentypen](how-to/java-to-sql-data-types.md).
- [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md) zum Registrieren einer externen Sprache (z. B. Java) in SQL Server.
- [Microsoft-Erweiterbarkeits-SDK für Java](how-to/extensibility-sdk-java-sql-server.md).
- Unter Windows und Linux kann mithilfe der Anweisung [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md) über eine externe Bibliothek auf Java-Code zugegriffen werden. Weitere Informationen: [Aufrufen von Java aus SQL Server](how-to/call-java-from-sql.md).
- [Java-Spracherweiterung](language-extensions-overview.md) unter Windows und Linux. Sie können kompilierten Java-Code für SQL Server zur Verfügung stellen, indem Sie Berechtigungen zuweisen und den Pfad festlegen. Client-Apps mit Zugriff auf SQL Server können Daten verwenden und durch Aufrufen von [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) Ihren Code ausführen. Dies ist dasselbe Verfahren, das auch für die R- und Python-Integration in SQL Server Machine Learning Services verwendet wird.

## <a name="next-steps"></a>Nächste Schritte

+ Installieren Sie die [SQL Server-Spracherweiterungen unter Windows](install/windows-java.md) oder [Linux](../linux/sql-server-linux-setup-language-extensions-java.md).
