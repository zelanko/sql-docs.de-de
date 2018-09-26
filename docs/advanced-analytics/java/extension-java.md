---
title: Java-spracherweiterung in SQL Server-2019 | Microsoft-Dokumentation
description: Führen Sie Java-Code, mit der Java-Sprache-Erweiterung von SQL Server 2019.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8acb0a72435306cdec8740ffb41ff499eea61fac
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715159"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Java-spracherweiterung in SQL Server-2019 

Ab SQL Server-2019, können Sie benutzerdefinierte Java-Code im Ausführen der [Erweiterungsframework](../concepts/extensibility-framework.md) als Add-on zu den Datenbank-Engine-Instanz. 

Das Extensibility Framework ist eine Architektur für die Ausführung von externen Codes: Java (ab SQL Server-2019), [Python (ab SQL Server 2017)](../concepts/extension-python.md), und [R (ab SQL Server 2016)](../concepts/extension-r.md). Ausführung von Code ist unabhängig von der Kern-Engine-Prozesse, aber vollständig in abfrageausführungsoption von SQL Server integriert. Dies bedeutet, dass das Verschieben von Daten aus jeder SQL Server-Abfrage in die externe Runtime, und nutzen oder Ergebnisse zurück in SQL Server beibehalten.

Wie bei jeder programming Language-Erweiterung, die gespeicherte Systemprozedur [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) ist die Schnittstelle für die vorkompilierten Java-Code ausführen.

## <a name="1---feature-installation"></a>1 - funktionsinstallation

Führen Sie Setup für SQL Server-2019 unter Windows oder Linux, die Java-Sprache-Erweiterung installieren. Eine Instanz von SQL Server-2019-Datenbank-Engine ist erforderlich. Java-Integration können keine früheren Versionen hinzugefügt werden.

Starten Sie auf Windows, die [Installations-Assistenten](../install/sql-machine-learning-services-windows-install.md). Wählen Sie im Funktionsauswahl **Machine Learning Services (datenbankintern)**. Obwohl die Java-Integration mit Machine Learning-Bibliotheken nicht geschaltet wird, ist dies die Option im Setup-Programm, das das Extensibility Framework bereitstellt. Sie können R und Python weglassen, wenn Sie möchten.

Installieren unter Linux, die [Datenbank-Engine](https://docs.microsoft.com/sql/linux/sql-server-linux-setup), als auch die [Erweiterbarkeit-Paket und Java-Erweiterungspaket](../../linux/sql-server-linux-setup-machine-learning.md).

Die folgenden Beispiele veranschaulichen die Syntax für jedes Linux-Betriebssystem.

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility
sudo apt-get install mssql-server-extensibility-java

# USE install commands
sudo zypper install mssql-server-extensibility
sudo zypper install mssql-server-extensibility-java
```

## <a name="2---configuration"></a>2 - Konfiguration

Konfigurieren Sie externen skriptausführung in der Datenbank-Engine-Instanz mit SQL Server Management Studio oder ein anderes Tool, das Transact-SQL-Skript ausgeführt wird.

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="3---bring-your-own-java"></a>3: bringen Sie Ihren eigenen Java

Ein Unterschied zu früheren sprachintegrationen wie R und Python ist, Sie-Steuerelement die JVM mit SQL Server verwendet wird.

| Java-version | Betriebssystem |
|--------------|------------------|
| [Java 1.10](http://jdk.java.net/10/)   | Windows |
| Java 1.8   | Linux | 

Erhalten, dass Java ist abwärtskompatibel, frühere Versionen funktionieren möglicherweise, aber die Versionen getesteten und unterstützten bei diesem frühen CTP-Version finden Sie in der Tabelle.

> [!Note]
>Zum Ausführen von Java mit SQL Server aus technischer Sicht müssen Sie nur die [Java Runtime Environment](http://www.oracle.com/technetwork/java/javase/downloads/jre10-downloads-4417026.html) (JRE) installiert. Das JDK wird eine Weiterentwicklung einschließlich der Java-Compiler und anderen Development Kit im Zusammenhang Pakete. Wenn Sie bereits eine Entwicklungsumgebung und nur eine Java-Laufzeit auf dem Servercomputer benötigen, ignorieren Sie die Anweisungen für die JDK-Installation, und nur installieren Sie JRE.

## <a name="jdk-on-windows"></a>JDK unter Windows

Laden Sie Windows-Version des der [Java SE Development Kit (JDK)](http://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html).

Installieren Sie das JDK unter der standardmäßigen/Program Dateien / Ordner sollten Sie vermeiden, gewähren zu lesen über die Berechtigung zum **alle ANWENDUNGSPAKETE** und **SQLRUserGroup** Sicherheitsgruppen auf einem alternativen Speicherort . Die gleiche Anweisungen gilt für den Zugriff auf Ihre Java-Classpath-Ordner, in dem Ihre .class oder JAR-Dateien gespeichert sind. 

> [!Note]
> Das Modell für Autorisierung und Isolation für Extensions wurde in dieser Version geändert. Weitere Informationen finden Sie unter [Unterschiede in einer SQL Server-Computer 2019 Learning Services-Installation](../install/sql-machine-learning-services-ver15.md).

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jdk-folder-windows-only"></a>Gewähren des Zugriffs auf nicht standardmäßige JDK-Ordner (nur Windows)

Sie können diesen Schritt überspringen, wenn Sie die JDK/JRE im Standardordner installiert. Führen Sie die folgenden PowerShell-Skripts, um Zugriff zu gewähren, für die Installation eines nicht standardmäßigen Ordner die **SQLRUsergroup** und SQL Server-Dienstkonten (in ALL_APPLICATION_PACKAGES) für den Zugriff auf die JVM und im Java-Classpath.

#### <a name="sqlrusergroup-permissions"></a>SQLRUserGroup-Berechtigungen

```powershell
$Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>"
$Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("SQLRUsergroup","FullControl","Allow")
$Acl.SetAccessRule($Ar)
Set-Acl ""<YOUR PATH TO JDK / CLASSPATH>" $Acl 
```

#### <a name="appcontainer-permissions"></a>AppContainer-Berechtigungen

```powershell
$Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>" 
$Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("ALL APPLICATION PACKAGES","FullControl","Allow") 
$Acl.SetAccessRule($Ar) 
Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
```

### <a name="add-the-jdk-path-to-javahome"></a>Fügen Sie den JDK-Pfad zum JAVA_HOME
Sie müssen auch eine Systemumgebungsvariable dem JDK/JRE-Installationspfad (z. B. "c:\Programme\Microsoft Files\Java\jdk-10.0.2") hinzugefügt werden, dass Sie den Namen "JAVA_HOME". 

Um eine Systemvariable zu erstellen, verwenden Sie die Systemsteuerung > System und Sicherheit > System den Zugriff auf **erweiterte Systemeigenschaften**. Klicken Sie auf **Umgebungsvariablen** und klicken Sie dann eine neue Systemvariable für JAVA_HOME erstellen.

![Für die Java Home-Umgebungsvariable](../media/java/env-variable-java-home.png "für Java-Setup")

## <a name="jdk-on-linux"></a>JDK unter Linux

Unter Linux installiert das Mssql-Server-Erweiterbarkeit-Java-Paket automatisch JRE 1.8, wenn es nicht bereits installiert ist. Es wird eine Umgebungsvariable namens JAVA_HOME auch die JVM-Pfad hinzufügen.

## <a name="limitations-in-ctp-20"></a>Einschränkungen in CTP 2.0

* Die Anzahl der Werte in den Eingabe- und Ausgabepuffer nicht überschreiten. `MAX_INT (2^31-1)` da dies die maximale Anzahl von Elementen ist, die in einem Array in Java zugeordnet werden können.

* Output-Parameter in Sp_execute_external_script werden in dieser Version nicht unterstützt.

* Keine LOB-Datentyp-Unterstützung für Eingabe- und Datasets in dieser Version. Finden Sie unter [Java und SQL Server-Datentypen](java-sql-datatypes.md) Einzelheiten über die Daten werden Typen in dieser CTP-Version unterstützt.

* Streaming mit dem Parameter Sp_execute_external_script @r_rowsPerRead wird in dieser CTP-Version nicht unterstützt.

* Partitionierung mit dem Parameter Sp_execute_external_script @input_data_1_partition_by_columns wird in dieser CTP-Version nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte

+ [Gewusst wie: Aufrufen von Java in SQL Server](howto-call-java-from-sql.md)
+ [Java-Beispiel in SQL Server](java-first-sample.md)
+ [Java und SQL Server-Datentypen](java-sql-datatypes.md)