---
title: Java-spracherweiterung in SQL Server-2019 – SQL Server Machine Learning Services
description: Installieren Sie, konfigurieren Sie und überprüfen Sie die Java-spracherweiterung 2019 für SQL Server für Linux und Windows-Systeme.
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a18886ea4daff3fb87853a556b67ad0562c2efd3
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017836"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Java-spracherweiterung in SQL Server-2019 

Ab SQL Server-2019 Preview unter Windows und Linux, können Sie benutzerdefinierte Java-Code im Ausführen der [Erweiterungsframework](../concepts/extensibility-framework.md) als Add-on zu den Datenbank-Engine-Instanz. 

Das Extensibility Framework ist eine Architektur für die Ausführung von externen Codes: (Ab SQL Server-2019), Java [Python (ab SQL Server 2017)](../concepts/extension-python.md), und [R (ab SQL Server 2016)](../concepts/extension-r.md). Ausführung von Code ist unabhängig von der Kern-Engine-Prozesse, aber vollständig in abfrageausführungsoption von SQL Server integriert. Dies bedeutet, dass das Verschieben von Daten aus jeder SQL Server-Abfrage in die externe Runtime, und nutzen oder Ergebnisse zurück in SQL Server beibehalten.

Wie bei jeder programming Language-Erweiterung, die gespeicherte Systemprozedur [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) ist die Schnittstelle für die vorkompilierten Java-Code ausführen.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Erforderliche Komponenten

Eine Instanz der SQL Server-2019 Preview ist erforderlich. Java-Integration keine frühere Versionen.

Java 8 wird unterstützt. Die Java Runtime Environment (JRE) ist die Mindestanforderung, aber JDKs sind nützlich, wenn Sie die Java-Compilers oder entwicklungspakete benötigen. Die JRE ist nicht erforderlich, da das JDK befindet sich alle Vorgänge, bei der Installation des JDK und.

Sie können die gewünschte Java 8-Verteilung verwenden. Im folgenden sind zwei, empfohlene Distributionen:

| Distribution | Java-version | Betriebssysteme | JDK | JRE |
|-|-|-|-|-|
| [Oracle Java SE](https://www.oracle.com/technetwork/java/javase/downloads/index.html) | 8 | Windows und Linux | Ja | Ja |
| [Zulu OpenJDK](https://www.azul.com/downloads/zulu/) | 8 | Windows und Linux | Ja | Nein |

Unter Linux die **Mssql-Server-Erweiterbarkeit – Java** Paket JRE 8 automatisch installiert wird, wenn es nicht bereits installiert ist. Installationsskripts fügen Sie der JVM-Pfad auch in eine Umgebungsvariable, die Namen JAVA_HOME hinzu.

Auf Windows, wir empfehlen die Installation von JDK unter der standardmäßigen `/Program Files/` Ordner nach Möglichkeit. Andernfalls ist zusätzlicher Konfiguration erforderlich, zum Gewähren von Berechtigungen für ausführbare Dateien. Weitere Informationen finden Sie unter den [Gewähren von Berechtigungen (Windows)](#perms-nonwindows) Abschnitt in diesem Dokument.

> [!Note]
> Erhalten, dass Java ist abwärtskompatibel, frühere Versionen funktionieren möglicherweise, aber die unterstützten und getestete Version für diese frühen CTP-Version ist Java 8. 

<a name="install-on-linux"></a>

## <a name="install-on-linux"></a>Installieren unter Linux

Installation kann die [Datenbank-Engine und die Java-Erweiterung zusammen](../../linux/sql-server-linux-setup-machine-learning.md#install-all), oder die Java-Unterstützung zu einer vorhandenen Instanz hinzufügen. In den folgenden Beispielen werden die Java-Erweiterung zu einer vorhandenen Installation hinzufügen.  

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility-java

# SUSE install commands
sudo zypper install mssql-server-extensibility-java
```

Bei der Installation **Mssql-Server-Erweiterbarkeit – Java**, das Paket automatisch JRE 8 installiert, wenn es nicht bereits installiert ist. Es wird eine Umgebungsvariable namens JAVA_HOME auch die JVM-Pfad hinzufügen.

Nach Abschluss der Installation, der nächste Schritt besteht [Konfigurieren der externen skriptausführung](#configure-script-execution).

> [!Note]
> Auf einem Gerät Internetverbindung paketabhängigkeiten heruntergeladen und installiert im Rahmen der Installation des Hauptpakets. Weitere Informationen, einschließlich der offline-Installation, finden Sie [installieren Sie SQL Server-Machine Learning unter Linux](../../linux/sql-server-linux-setup-machine-learning.md).

### <a name="grant-permissions-on-linux"></a>Erteilen von Berechtigungen für Linux

Um SQL Server mit Berechtigungen zum Ausführen der Java-Klassen zu gewährleisten, müssen Sie Berechtigungen festlegen.

Zum Gewähren von Lese- und führen Sie den Zugriff auf Dateien oder Klassendateien jar, führen Sie den folgenden **Chmod** -Befehl für jede Klasse oder JAR-Datei. Es wird empfohlen, die Klassendateien in eine JAR-Datei einfügen, bei der Arbeit mit SQL Server. Hilfe, die eine JAR-Datei erstellen, finden Sie unter [Vorgehensweise: Erstellen Sie eine JAR-Datei](#create-jar).

```cmd
chmod ug+rx <MyJarFile.jar>
```
Außerdem müssen Sie für das Verzeichnis "oder" JAR-Datei zum Lesen/Ausführen Mssql_satellite-Berechtigungen zu erteilen.

* Wenn Sie Klassendateien aus SQL Server aufrufen, Mssql_satellite wird müssen Read/execute-Berechtigungen für *jeder* in der Ordnerhierarchie vom Stamm auf dem direkt übergeordneten Verzeichnis.

* Wenn Sie eine JAR-Datei von SQL Server aufrufen, ist es ausreichend, um den Befehl auf die JAR-Datei selbst ausführen.

```cmd
chown mssql_satellite:mssql_satellite <directory>
```

```cmd
chown mssql_satellite:mssql_satellite <MyJarFile.jar>
```

<a name="install-on-windows"></a>

## <a name="install-on-windows"></a>Install on Windows (Unter Windows installieren)

1. Stellen Sie sicher, dass eine unterstützte Version von Java installiert ist. Weitere Informationen finden Sie unter den [Voraussetzungen](#prerequisites).

2. [Führen Sie Setup](../install/sql-machine-learning-services-windows-install.md) zum Installieren von SQL Server-2019.

3. Wenn Sie zur Auswahl von Features gelangen, wählen Sie **Machine Learning Services (datenbankintern)**. 

   Obwohl die Java-Integration mit Machine Learning-Bibliotheken nicht geschaltet wird, ist dies die Option im Setup-Programm, das das Extensibility Framework bereitstellt. Sie können R und Python weglassen, wenn Sie möchten.

4. Beenden Sie den Installationsassistenten, und fahren Sie mit der nächsten zwei Aufgaben.

### <a name="add-the-javahome-variable"></a>Fügen Sie die JAVA_HOME-variable

JAVA_HOME ist eine Umgebungsvariable, die den Speicherort des Java-Interpreter angibt. Erstellen Sie in diesem Schritt eine Systemumgebungsvariable für auf Windows.

1. Suchen und kopieren Sie den JDK/JRE-Pfad (z. B. `C:\Program Files\Java\jdk1.8.0_201`).

    Abhängig von Ihrer bevorzugten Java-Distribution möglicherweise anders als die oben genannten Beispiel-Pfad Ihren Standort des JDK oder JRE.

2. Öffnen Sie in der Systemsteuerung **System und Sicherheit**öffnen **System**, und klicken Sie auf **erweiterte Systemeigenschaften**.

3. Klicken Sie auf **Umgebungsvariablen**.

4. Erstellen Sie eine neue Systemvariable für `JAVA_HOME` mit dem Wert des JDK/JRE-Pfads (gefunden in Schritt 1).

5. Starten Sie neu [Launchpad](../concepts/extensibility-framework.md#launchpad).

    1. Öffnen Sie den [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md).

    2. Klicken Sie unter SQL Server-Dienste, mit der rechten Maustaste in SQL Server Launchpad, und wählen Sie **Neustart**.

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jdk-folder-windows-only"></a>Gewähren des Zugriffs auf nicht standardmäßige JDK-Ordner (nur Windows)

Sie können diesen Schritt überspringen, wenn Sie die JDK/JRE im Standardordner installiert. 

Führen Sie für die Installation eines nicht standardmäßigen Ordner die **Icacls** -Befehle über eine *mit erhöhten Rechten* Zeile gewähren Zugriff auf die **SQLRUsergroup** und SQL Server-Dienstkonten (in  **ALL_APPLICATION_PACKAGES**) für den Zugriff auf die JVM und im Java-Classpath. Die Befehle werden rekursiv gewähren des Zugriffs auf alle Dateien und Ordner im Pfad angegebene Verzeichnis.

#### <a name="sqlrusergroup-permissions"></a>SQLRUserGroup-Berechtigungen

Für eine benannte Instanz, die den Namen der Instanz an SQLRUsergroup anfügen (z. B. `SQLRUsergroupINSTANCENAME`).

```cmd
icacls "<PATH TO CLASS or JAR FILES>" /grant "SQLRUsergroup":(OI)(CI)RX /T
```

#### <a name="appcontainer-permissions"></a>AppContainer-Berechtigungen

```cmd
icacls "PATH to JDK/JRE" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T
```

<a name="configure-script-execution"></a>

## <a name="configure-script-execution"></a>Konfigurieren Sie die Ausführung des Skripts

An diesem Punkt sind Sie fast bereit, die Java-Code unter Linux oder Windows ausgeführt werden. Wechseln Sie zu SQL Server Management Studio oder ein anderes Tool, das Transact-SQL-Skript zum Aktivieren der externen skriptausführung ausgeführt wird, als letzten Schritt.

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="verify-installation"></a>Überprüfen der Installation

Klicken Sie zum Bestätigen die Installation betriebsbereit ist, erstellen und Ausführen einer [beispielanwendung](java-first-sample.md) verwenden das JDK, die Sie gerade installiert haben, platzieren die Dateien in den Klassenpfad, die Sie zuvor konfiguriert haben.

## <a name="differences-in-ctp-23"></a>Unterschiede in der CTP-Version 2.3

Wenn Sie bereits mit Machine Learning Services vertraut sind, wurde das Modell für Autorisierung und Isolation für Erweiterungen in dieser Version geändert. Weitere Informationen finden Sie unter [Unterschiede in einer SQL Server-Computer 2019 Learning Services-Installation](../install/sql-machine-learning-services-ver15.md).

## <a name="limitations-in-ctp-23"></a>Einschränkungen in CTP 2.3

* Die Anzahl der Werte in den Eingabe- und Ausgabepuffer nicht überschreiten. `MAX_INT (2^31-1)` da dies die maximale Anzahl von Elementen ist, die in einem Array in Java zugeordnet werden können.

* Ausgabeparameter in [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) werden in dieser Version nicht unterstützt.

* Streaming mit dem Parameter Sp_execute_external_script @r_rowsPerRead wird in dieser CTP-Version nicht unterstützt.

* Partitionierung mit dem Parameter Sp_execute_external_script @input_data_1_partition_by_columns wird in dieser CTP-Version nicht unterstützt.

<a name="create-jar"></a>

## <a name="how-to-create-a-jar-file-from-class-files"></a>Vorgehensweise: Erstellen Sie eine JAR-Datei aus Klassendateien

Navigieren Sie zum Ordner, der die Klassendatei ein, und führen Sie diesen Befehl:

```cmd
jar -cf <MyJar.jar> *.class
```

Stellen Sie sicher, dass den Pfad zur **jar.exe** gehört die Systemvariable Path. Alternativ geben Sie den vollständigen Pfad zur JAR-Datei, die sich unter "/ bin" im Ordner "JDK" befinden: `C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class`

## <a name="next-steps"></a>Nächste Schritte

+ [Gewusst wie: Aufrufen von Java in SQL Server](howto-call-java-from-sql.md)
+ [Java-Beispiel in SQL Server](java-first-sample.md)
+ [Java und SQL Server-Datentypen](java-sql-datatypes.md)