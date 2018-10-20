---
title: Java-spracherweiterung in SQL Server-2019 | Microsoft-Dokumentation
description: Führen Sie Java-Code, mit der Java-Sprache-Erweiterung von SQL Server 2019.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/12/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2d69a255c56c3b15051a393b74eb1492a4f830f4
ms.sourcegitcommit: 93e3bb8941411b808e00daa31121367e96fdfda1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "49359337"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Java-spracherweiterung in SQL Server-2019 

Ab SQL Server-2019, können Sie benutzerdefinierte Java-Code im Ausführen der [Erweiterungsframework](../concepts/extensibility-framework.md) als Add-on zu den Datenbank-Engine-Instanz. 

Das Extensibility Framework ist eine Architektur für die Ausführung von externen Codes: Java (ab SQL Server-2019), [Python (ab SQL Server 2017)](../concepts/extension-python.md), und [R (ab SQL Server 2016)](../concepts/extension-r.md). Ausführung von Code ist unabhängig von der Kern-Engine-Prozesse, aber vollständig in abfrageausführungsoption von SQL Server integriert. Dies bedeutet, dass das Verschieben von Daten aus jeder SQL Server-Abfrage in die externe Runtime, und nutzen oder Ergebnisse zurück in SQL Server beibehalten.

Wie bei jeder programming Language-Erweiterung, die gespeicherte Systemprozedur [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) ist die Schnittstelle für die vorkompilierten Java-Code ausführen.

## <a name="prerequisites"></a>Erforderliche Komponenten

Eine SQL Server-2019 ist erforderlich. Java-Integration keine frühere Versionen. 

Java-versionsanforderungen variieren für Windows und Linux. Die Java Runtime Environment (JRE) ist die Mindestanforderung, aber JDKs sind nützlich, wenn Sie die Java-Compilers oder entwicklungspakete benötigen. Die JRE ist nicht erforderlich, da das JDK befindet sich alle Vorgänge, bei der Installation des JDK und.

| Betriebssystem | Java-version | JRE herunterladen | JDK-download |
|------------------|--------------|--------------|--------------|
| Windows          | 1.10         | [JRE-10](http://www.oracle.com/technetwork/java/javase/downloads/jre10-downloads-4417026.html) | [JDK-10](http://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html)  |
| Linux            | 1.8          |  [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) | [JDK 8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  |  

Unter Linux die **Mssql-Server-Erweiterbarkeit – Java** Paket JRE 1.8 automatisch installiert wird, wenn es nicht bereits installiert ist. Installationsskripts fügen Sie der JVM-Pfad auch in eine Umgebungsvariable, die Namen JAVA_HOME hinzu.

Auf Windows, wir empfehlen die Installation von JDK unter der standardmäßigen/Program Dateien / Ordner "" Wenn möglich. Andernfalls ist zusätzlicher Konfiguration erforderlich, zum Gewähren von Berechtigungen für ausführbare Dateien. Weitere Informationen finden Sie unter den [Gewähren von Berechtigungen (Windows)](#perms-nonwindows) Abschnitt in diesem Dokument.

> [!Note]
> Erhalten, dass Java ist abwärtskompatibel, frühere Versionen funktionieren möglicherweise, aber die Versionen getesteten und unterstützten bei diesem frühen CTP-Version finden Sie in der Tabelle.

<a name="install-on-linux"></a>

## <a name="install-on-linux"></a>Installieren unter Linux

Installation kann die [Datenbank-Engine und die Java-Erweiterung zusammen](../../linux/sql-server-linux-setup-machine-learning.md#chained-installation), oder die Java-Unterstützung zu einer vorhandenen Instanz hinzufügen. In den folgenden Beispielen werden die Java-Erweiterung zu einer vorhandenen Installation hinzufügen.  

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility-java

# USE install commands
sudo zypper install mssql-server-extensibility-java
```

Bei der Installation **Mssql-Server-Erweiterbarkeit – Java**, das Paket installiert automatisch JRE 1.8, wenn es nicht bereits installiert ist. Es wird eine Umgebungsvariable namens JAVA_HOME auch die JVM-Pfad hinzufügen.

Nach Abschluss der Installation, der nächste Schritt besteht [Konfigurieren der externen skriptausführung](#configure-script-execution).

> [!Note]
> Auf einem Gerät Internetverbindung paketabhängigkeiten heruntergeladen und installiert im Rahmen der Installation des Hauptpakets. Weitere Informationen, einschließlich der offline-Installation, finden Sie [installieren Sie SQL Server-Machine Learning unter Linux](../../linux/sql-server-linux-setup-machine-learning.md).

<a name="install-on-windows"></a>

## <a name="install-on-windows"></a>Install on Windows (Unter Windows installieren)

1. [Führen Sie Setup](../install/sql-machine-learning-services-windows-install.md) zum Installieren von SQL Server-2019.

2. Wenn Sie zur Auswahl von Features gelangen, wählen Sie **Machine Learning Services (datenbankintern)**. 

   Obwohl die Java-Integration mit Machine Learning-Bibliotheken nicht geschaltet wird, ist dies die Option im Setup-Programm, das das Extensibility Framework bereitstellt. Sie können R und Python weglassen, wenn Sie möchten.

3. Beenden Sie den Installationsassistenten, und fahren Sie mit der nächsten zwei Aufgaben.

### <a name="add-the-javahome-variable"></a>Fügen Sie die JAVA_HOME-variable

JAVA_HOME ist eine Umgebungsvariable, die den Speicherort des Java-Interpreter angibt. Erstellen Sie in diesem Schritt eine Systemumgebungsvariable für auf Windows.

1. Suchen Sie und kopieren Sie den JDK/JRE-Installationspfad (z. B. c:\Programme\Microsoft Files\Java\jdk-10.0.2).

  In CTP 2.0 funktioniert durch Festlegen von JAVA_HOME auf den Basis-Jdk-Ordner nur für Java 1.10. 

  Für Java 1.8 erweitern Sie den Pfad zum Erreichen der jvm.dll auf Windows in Ihr JDK-Paket (beispielsweise "c:\Programme\Microsoft Files\Java\jdk1.8.0_181\bin\server". Sie können auch auf einen Basisordner für JRE verweisen: "C:\Programme\Microsoft Files\Java\jre1.8.0_181".

2. Öffnen Sie in der Systemsteuerung **System und Sicherheit**öffnen **System**, und klicken Sie auf **erweiterte Systemeigenschaften**.

3. Klicken Sie auf **Umgebungsvariablen**.

4. Erstellen Sie eine neue Systemvariable für JAVA_HOME ein.

   ![Für die Java Home-Umgebungsvariable](../media/java/env-variable-java-home.png "für Java-Setup")

<a name="perms-nonwindows"></a>

### <a name="grant-permissions-to-java-executables"></a>Gewähren von Berechtigungen für ausführbare Java-Dateien

Standardmäßig das Konto, unter dem externe Prozessen ausgeführt werden, nicht auf JRE oder ein JDK-Dateien zugreifen. Führen Sie in diesem Abschnitt das folgende PowerShell-Skript zum Gewähren von Berechtigungen für den Zugriff zulassen.

1. Suchen Sie und kopieren Sie den Speicherort der JDK oder JRE-Installation. Es kann z. B. c:\Programme\Microsoft Files\Java\jdk-10.0.2 sein.

2. Öffnen Sie PowerShell mit Administratorrechten aus. Wenn Sie mit dieser Aufgabe nicht vertraut sind, finden Sie unter [in diesem Artikel](https://www.top-password.com/blog/5-ways-to-run-powershell-as-administrator-in-windows-10/) Tipps.

3. Führen Sie das folgende Skript zum Erteilen von **SQLRUserGroup** Berechtigungen auf die Java-Dateien. 

  **SQLRUserGroup** gibt an, die Berechtigungen der externen Prozessen ausgeführt. Standardmäßig Mitglied dieser Gruppe über die Berechtigung für die R- und Python-Programmdateien installiert, indem Sie SQL Server, jedoch nicht in Java. Geben Sie zum Ausführen von Java ausführbare Dateien **SQLRUserGroup** Berechtigung.

   ```powershell
   $Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>"
   $Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("SQLRUsergroup","FullControl","Allow")
   $Acl.SetAccessRule($Ar)
   Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
   ```
4. Führen Sie das folgende Skript zum Erteilen von **alle ANWENDUNGSPAKETE** sowie Berechtigungen. 

  In SQL Server-2019, ersetzen Container workerkonten als der Isolationsmechanismus mit Prozessen, die ausgeführt wird, innerhalb von Containern, unter der Identität des Launchpad-Dienstkontos, das Member ist der **SQLRUserGroup**. Weitere Informationen finden Sie unter [installieren Sie die Unterschiede in einer SQL Server-2019](../install/sql-machine-learning-services-ver15.md).

   ```powershell
   $Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>" 
   $Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("ALL APPLICATION PACKAGES","FullControl","Allow") 
   $Acl.SetAccessRule($Ar) 
   Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
   ```

5. Wiederholen Sie die vorherigen beiden Schritte für alle Java-Classpath-Ordner mit den .class oder JAR-Dateien, die auf SQL Server ausgeführt werden soll. Wenn Sie Ihre kompilierte Programme in einem Pfad wie C:\JavaPrograms\my-app beibehalten, z. B. gewähren **SQLRUserGroup** und **alle ANWENDUNGSPAKETE** -Berechtigung für den Ordner, damit die Programme, die geladen werden können.

  Achten Sie darauf, dass zum Gewähren von Berechtigungen auf den vollständigen Pfad, in den Stammordner ab. Berechtigung für nur den enthaltenden Ordner nicht ausreichend, damit Ihr Code geladen.

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

## <a name="differences-in-ctp-20"></a>Unterschiede in der CTP-Version 2.0

Wenn Sie bereits mit Machine Learning Services vertraut sind, wurde das Modell für Autorisierung und Isolation für Erweiterungen in dieser Version geändert. Weitere Informationen finden Sie unter [Unterschiede in einer SQL Server-Computer 2019 Learning Services-Installation](../install/sql-machine-learning-services-ver15.md).

## <a name="limitations-in-ctp-20"></a>Einschränkungen in CTP 2.0

* Die Anzahl der Werte in den Eingabe- und Ausgabepuffer nicht überschreiten. `MAX_INT (2^31-1)` da dies die maximale Anzahl von Elementen ist, die in einem Array in Java zugeordnet werden können.

* Ausgabeparameter in [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) werden in dieser Version nicht unterstützt.

* Keine LOB-Datentyp-Unterstützung für Eingabe- und Datasets in dieser Version. Finden Sie unter [Java und SQL Server-Datentypen](java-sql-datatypes.md) Einzelheiten über die Daten werden Typen in dieser CTP-Version unterstützt.

* Streaming mit dem Parameter Sp_execute_external_script @r_rowsPerRead wird in dieser CTP-Version nicht unterstützt.

* Partitionierung mit dem Parameter Sp_execute_external_script @input_data_1_partition_by_columns wird in dieser CTP-Version nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte

+ [Gewusst wie: Aufrufen von Java in SQL Server](howto-call-java-from-sql.md)
+ [Java-Beispiel in SQL Server](java-first-sample.md)
+ [Java und SQL Server-Datentypen](java-sql-datatypes.md)