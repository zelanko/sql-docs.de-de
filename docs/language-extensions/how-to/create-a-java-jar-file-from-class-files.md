---
title: Erstellen einer Java-JAR-Datei aus Klassendateien
titleSuffix: SQL Server Language Extensions
description: Erfahren Sie, wie Sie eine Java-JAR-Datei aus Klassendateien erstellen.
author: dphansen
ms.author: davidph
ms.date: 07/25/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4cec311a28f9d5119b5a0aeb696597e8b34ba25a
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2019
ms.locfileid: "73588774"
---
# <a name="create-a-java-jar-file-from-class-files"></a>Erstellen einer Java-JAR-Datei aus Klassendateien
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Wenn Sie [SQL Server-Spracherweiterungen](../language-extensions-overview.md) verwenden und Java-Code ausführen, empfiehlt es sich, die Klassendateien in eine JAR-Datei zu packen.

## <a name="create-a-jar-file"></a>Erstellen einer JAR-Datei

Um eine JAR-Datei aus Klassendateien zu erstellen, navigieren zu dem Ordner, der Ihre Klassendatei enthält, und führen Sie den folgenden Befehl aus:

```cmd
jar -cf <MyJar.jar> *.class
```

Stellen Sie sicher, dass der Pfad zu `jar.exe` Teil der Systempfadvariable ist. Alternativ dazu können Sie auch den vollständigen Pfad zur JAR-Datei angeben, den Sie im JDK-Ordner unter `/bin` finden. Beispiel:

```cmd
C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class
```

## <a name="next-steps"></a>Nächste Schritte

+ [Aufrufen von Java in SQL Server](../how-to/call-java-from-sql.md)