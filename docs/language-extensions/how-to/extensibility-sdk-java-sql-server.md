---
title: Microsoft-Erweiterbarkeits-SDK für Java für SQL Server
description: Erfahren Sie, wie Sie mit dem Microsoft-Erweiterbarkeits-SDK für Java ein Java-Programm für SQL Server implementieren.
ms.prod: sql
ms.technology: language-extensions
ms.date: 08/21/2019
ms.topic: conceptual
author: nelgson
ms.author: negust
ms.reviewer: dphansen
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f2c1e7eb5b5410ad0c12b8dec6f451b7572f0e36
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "73588794"
---
# <a name="microsoft-extensibility-sdk-for-java-for-sql-server"></a>Microsoft-Erweiterbarkeits-SDK für Java für SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel beschreibt, wie Sie mit dem Microsoft-Erweiterbarkeits-SDK für Java ein Java-Programm für SQL Server implementieren können. Das SDK ist eine Schnittstelle für die Java-Spracherweiterung, die zum Austauschen von Daten mit SQL Server und zum Ausführen von Java-Code aus SQL Server verwendet wird.

Das SDK wird als Teil von SQL Server 2019 Release Candidate 1 sowohl unter Windows als auch unter Linux installiert:

+ Standardinstallationspfad unter Windows: **[Basisverzeichnis der Instanzinstallation]\MSSQL\Binn\mssql-java-lang-extension.jar**
+ Standardinstallationspfad unter Linux: **/opt/mssql/lib/mssql-java-lang-extension.jar**

Es handelt sich um Open-Source-Code, der im [GitHub-Repository für SQL Server-Spracherweiterungen](https://github.com/microsoft/sql-server-language-extensions) zur Verfügung steht.

## <a name="implementation-requirements"></a>Anforderungen an die Implementierung

Die SDK-Schnittstelle definiert eine Reihe von Anforderungen, die erfüllt sein müssen, damit SQL Server mit der Java-Runtime kommunizieren kann. Um das SDK zu verwenden, müssen Sie in Ihrer Hauptklasse einige Implementierungsregeln befolgen. SQL Server kann dann eine bestimmte Methode in der Java-Klasse ausführen und über die Java-Spracherweiterung Daten austauschen.

Ein Beispiel für die Verwendung des SDKs finden Sie unter [Tutorial: Suchen nach einer Zeichenfolge mithilfe regulärer Ausdrücke (RegEx) in Java](../tutorials/search-for-string-using-regular-expressions-in-java.md).

## <a name="sdk-classes"></a>SDK-Klassen

Das SDK besteht aus drei Klassen.

Zwei abstrakte Klassen definieren die Schnittstelle, die von der Java-Erweiterung zum Austauschen von Daten mit SQL Server verwendet wird:

- **AbstractSqlServerExtensionExecutor**
- **AbstractSqlServerExtensionDataset**

Die dritte Klasse ist eine Hilfsklasse, die eine Implementierung eines Datasetobjekts enthält. Es handelt sich um eine optionale Klasse, die Sie verwenden können, um sich den Einstieg zu erleichtern. Sie können stattdessen auch eine eigene Implementierung einer solchen Klasse verwenden.

- **PrimitiveDataset**

Im Folgenden finden Sie Beschreibungen jeder Klasse im SDK. Der Quellcode der SDK-Klassen ist im [GitHub-Repository für SQL Server-Spracherweiterungen](https://github.com/microsoft/sql-server-language-extensions/tree/master/language-extensions/java/sdk) verfügbar.

### <a name="class-abstractsqlserverextensionexecutor"></a>Klasse: AbstractSqlServerExtensionExecutor

Die abstrakte Klasse **AbstractSqlServerExtensionExecutor** enthält die Schnittstelle, die von der Java-Spracherweiterung für SQL Server zum Ausführen von Java-Code verwendet wird.

Ihre Java-Hauptklasse muss von dieser Klasse erben. Dies bedeutet, dass die Klasse bestimmte Methoden enthält, die Sie in Ihrer eigenen Klasse implementieren müssen.

Damit Ihre Klasse von dieser abstrakten Klasse erben kann, erweitern Sie Ihre Klasse in der Klassendeklaration um den Namen der abstrakten Klasse:

```java
public class <MyClass> extends AbstractSqlServerExtensionExecutor {}
```

Ihre Hauptklasse muss mindestens die Methode „execute(...)“ implementieren.

#### <a name="method-execute"></a>execute-Methode

Die execute-Methode ist die Methode, die von SQL Server über die Java-Spracherweiterung aufgerufen wird, um Java-Code aus SQL Server aufzurufen. Es handelt sich um eine Schlüsselmethode, in der Sie die Hauptvorgänge einschließen, die Sie aus SQL Server ausführen möchten.

Zum Übergeben von Methodenargumenten von SQL Server an Java verwenden Sie den `@param`-Parameter in `sp_execute_external_script`. Die **execute**-Methode akzeptiert ihre Argumente auf diese Weise.

```java
public AbstractSqlServerExtensionDataset execute(AbstractSqlServerExtensionDataset input, LinkedHashMap<String, Object> params)  {}
```

#### <a name="method-init"></a>init-Methode

Die init-Methode wird nach dem Konstruktor und vor der execute-Methode ausgeführt. Alle Vorgänge, die vor „execute(...)“ ausgeführt werden müssen, können in dieser Methode ausgeführt werden.

```java
public void init(String sessionId, int taskId, int numtask) {}
```

### <a name="class-abstractsqlserverextensiondataset"></a>Klasse: AbstractSqlServerExtensionDataset

Die abstrakte Klasse **AbstractSqlServerExtensionDataset** enthält die Schnittstelle für die Verarbeitung von Eingabe- und Ausgabedaten, die von der Java-Erweiterung verwendet wird.


### <a name="class-primitivedataset"></a>Klasse: PrimitiveDataset

Die Klasse **PrimitiveDataset** ist eine Implementierung der Klasse **AbstractSqlServerExtensionDataset**, die einfache Typen als primitive Arrays speichert.

Sie wird im SDK einfach als optionale Hilfsklasse bereitgestellt. Wenn Sie diese Klasse nicht verwenden, müssen Sie selbst eine Klasse implementieren, die von **AbstractSqlServerExtensionDataset** erbt.  

## <a name="next-steps"></a>Nächste Schritte

+ [Tutorial: Suchen nach einer Zeichenfolge mithilfe regulärer Ausdrücke (RegEx) in Java](../tutorials/search-for-string-using-regular-expressions-in-java.md)
+ [Aufrufen von Java in SQL Server](call-java-from-sql.md)
