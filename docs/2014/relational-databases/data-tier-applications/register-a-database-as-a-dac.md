---
title: Registrieren einer Datenbank als eine DAC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerdacwizard.registerdac.f1
- sql12.swb.registerdacwizard.summary.f1
- sql12.swb.registerdacwizard.introduction.f1
- sql12.swb.registerdacwizard.setproperties.f1
helpviewer_keywords:
- wizard [DAC], register
- How to [DAC], register
- register DAC
- data-tier application [SQL Server], register
ms.assetid: 08e52aa6-12f3-41dd-a793-14b99a083fd5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1b33e0d78dfe308c537ea5297b55415bce304474
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54129418"
---
# <a name="register-a-database-as-a-dac"></a>Registrieren einer Datenbank als eine DAC
  Verwenden Sie entweder die **Datenebenen-Assistenten zum Registrieren von** oder ein Windows PowerShell-Skript, um eine Definition der von datenebenenanwendungen (DACs) zu erstellen, die die Objekte in einer vorhandenen Datenbank beschreibt, und registrieren die DAC-Definition in der `msdb` -Systemdatenbank (**master** in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]).  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#LimitationsRestrictions), [Berechtigungen](#Permissions)  
  
-   **So aktualisieren Sie eine DAC mit:**  [Die Assistenten zum Registrieren von datenebenenanwendungen](#UsingRegisterDACWizard), [PowerShell](#RegisterDACPowerShell)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Beim Registrierungsprozess wird eine DAC-Definition erstellt, die die Objekte in der Datenbank definiert. Eine DAC-Instanz setzt sich aus der Kombination von DAC-Definition und Datenbank zusammen. Bei der Registrierung einer Datenbank als DAC in einer verwalteten Instanz der Datenbank-Engine wird die registrierte DAC in das SQL Server-Hilfsprogramm integriert, wenn der Hilfsprogramm-Sammlungssatz das nächste Mal von der Instanz an den Steuerungspunkt für das Hilfsprogramm gesendet wird. Die DAC ist dann unter dem Knoten **Bereitgestellte Datenschichtanwendungen** im [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Bereitgestellte Datenschichtanwendungen** details page.  
  
###  <a name="LimitationsRestrictions"></a> Einschränkungen  
 Die DAC-Registrierung kann nur für eine Datenbank in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]oder [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) oder höher ausgeführt werden. Die DAC-Registrierung ist nicht möglich, wenn eine DAC bereits für die Datenbank registriert ist. Wenn die Datenbank durch Bereitstellung einer DAC erstellt wurde, kann der **Assistent zum Registrieren von Datenschichtanwendungen**beispielsweise nicht ausgeführt werden.  
  
 Es kann keine DAC registriert werden, wenn die Datenbank Objekte, die in einer DAC nicht unterstützt werden, oder enthaltene Benutzer enthält. Weitere Informationen zu den in einer DAC unterstützten Objekttypen finden Sie unter [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).  
  
###  <a name="Permissions"></a> Berechtigungen  
 Zum Registrieren einer DAC in einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] sind mindestens die ALTER ANY LOGIN-Berechtigung und die VIEW DEFINITION-Berechtigung im Datenbankbereich sowie SELECT-Berechtigungen für **sys.sql_expression_dependencies**und die Mitgliedschaft in der festen Serverrolle **dbcreator** erforderlich. Mitglieder der festen Serverrolle **sysadmin** oder des integrierten SQL Server-Systemadministratorkontos **sa** sind ebenfalls zum Registrieren einer DAC berechtigt. Zum Registrieren einer DAC, die keine Anmeldungen in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] enthält, müssen Sie Mitglied der Rollen **dbmanager** oder **serveradmin** sein. Zum Registrieren einer DAC, die Anmeldungen in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] enthält, müssen Sie Mitglied der Rollen **loginmanager** oder **serveradmin** sein.  
  
##  <a name="UsingRegisterDACWizard"></a> Verwenden des Assistenten zum Registrieren von Datenebenenanwendungen  
 **So registrieren Sie eine DAC mithilfe eines Assistenten**  
  
1.  Erweitern Sie im **Objekt-Explorer**den Knoten für die Instanz, die die Datenbank enthält, die als DAC registriert werden soll.  
  
2.  Erweitern Sie den Knoten **Datenbanken** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die zu registrierende Datenbank, zeigen Sie auf **Tasks**, und wählen Sie dann **Als Datenschichtanwendung registrieren…** aus.  
  
4.  Bearbeiten Sie die Dialogfenster des Assistenten:  
  
    1.  [Seite "Einführung"](#Introduction)  
  
    2.  [Seite "Eigenschaften festlegen"](#Set_properties)  
  
    3.  [Seite "Überprüfung und Zusammenfassung"](#Summary)  
  
    4.  [Seite "DAC registrieren"](#Register)  
  
##  <a name="Introduction"></a> Seite "Einführung"  
 Auf dieser Seite werden die Schritte zum Registrieren einer Datenebenenanwendung beschrieben.  
  
 **Diese Seite nicht mehr anzeigen.** – Aktivieren Sie dieses Kontrollkästchen, damit die Seite in Zukunft nicht mehr angezeigt wird.  
  
 **Weiter >** – Geht zur Seite **Eigenschaften festlegen** über.  
  
 **Abbrechen** – Beendet den Assistenten, ohne eine DAC zu registrieren.  
  
##  <a name="Set_properties"></a> Seite "Eigenschaften festlegen"  
 Verwenden Sie diese Seite, um Eigenschaften auf DAC-Ebene anzugeben, z. B. den Anwendungsnamen und die Version.  
  
 **Anwendungsname** – Eine Zeichenfolge mit dem Namen, der die DAC-Definition identifiziert. Das Feld enthält den Namen der Datenbank.  
  
 **Version** – Ein numerischer Wert, der die Version der DAC identifiziert. Die DAC-Version wird in Visual Studio verwendet, um die Version der DAC zu identifizieren, an der die Entwickler arbeiten. Wenn Sie eine DAC bereitstellen möchten, befindet sich die Version in der `msdb` Datenbank und kann später unter angezeigt werden die **Data-Tier-Anwendungen** Knoten im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Beschreibung** – Optional. Ein Text, der den Zweck der DAC erläutert. Wenn Sie eine DAC bereitstellen möchten, befindet sich die Beschreibung in der `msdb` Datenbank und kann später unter angezeigt werden die **Data-Tier-Anwendungen** Knoten im [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 **\< Vorherige** -wird wieder die **Einführung** Seite.  
  
 **Weiter >** – Überprüft, ob eine DAC aus den in der Datenbank enthaltenen Objekten erstellt werden kann, und zeigt die Ergebnisse auf der Seite **Überprüfung und Zusammenfassung** an.  
  
 **Abbrechen** – Beendet den Assistenten, ohne die DAC zu registrieren.  
  
##  <a name="Summary"></a> Seite "Überprüfung und Zusammenfassung"  
 Verwenden Sie diese Seite, um die Aktionen zu überprüfen, die der Assistent beim Registrieren der DAC ausführt. Die Seite durchläuft drei Statusübergänge, während überprüft wird, ob eine DAC aus den in der Datenbank enthaltenen Objekten erstellt werden kann.  
  
### <a name="retrieving-objects"></a>Abrufen von Objekten  
 **Datenbank- und Serverobjekte werden abgerufen.** – Zeigt eine Statusanzeige an, während der Assistent alle erforderlichen Objekte aus der Datenbank und der Instanz der Datenbank-Engine abruft.  
  
 **\< Vorherige** -wird wieder die **Eigenschaften** Seite, um Ihre Einträge ändern.  
  
 **Weiter >** – Registriert die DAC und zeigt die Ergebnisse auf der Seite **DAC registrieren** an.  
  
 **Abbrechen** – Beendet den Assistenten, ohne die DAC zu registrieren.  
  
### <a name="validating-objects"></a>Überprüfen von Objekten  
 **Checking**  _SchemaName_ **.** _ObjectName_ **.** – Zeigt eine Statusanzeige an, während der Assistent die Abhängigkeiten der abgerufenen Objekten überprüft und sicherstellt, dass sie alle für eine DAC gültig sind. _SchemaName_**.**_ObjectName_ gibt das derzeit überprüfte Objekt an.  
  
 **\< Vorherige** -wird wieder die **Eigenschaften** Seite, um Ihre Einträge ändern.  
  
 **Weiter >** – Registriert die DAC und zeigt die Ergebnisse auf der Seite **DAC registrieren** an.  
  
 **Abbrechen** – Beendet den Assistenten, ohne die DAC zu registrieren.  
  
### <a name="summary"></a>Zusammenfassung  
 **Die folgende Einstellung wird verwendet, um die DAC zu registrieren.** – Zeigt einen Bericht der Eigenschaften und Objekte an, die in der DAC enthalten sind.  
  
 **Bericht speichern** – Klicken Sie auf diese Schaltfläche, um eine Kopie des Überprüfungsberichts in einer HTML-Datei zu speichern. Der Standardordner ist ein Ordner **SQL Server Management Studio\DAC Packages** im Ordner „Dokumente“ unter Ihrem Windows-Konto.  
  
 **\< Vorherige** -wird wieder die **Eigenschaften** Seite, um Ihre Einträge ändern.  
  
 **Weiter >** – Registriert die DAC und zeigt die Ergebnisse auf der Seite **DAC registrieren** an.  
  
 **Abbrechen** – Beendet den Assistenten, ohne die DAC zu registrieren.  
  
##  <a name="Register"></a> Seite "DAC registrieren"  
 Auf dieser Seite wird angegeben, ob der Registrierungsvorgang erfolgreich war oder fehlgeschlagen ist.  
  
 **Die DAC wird registriert** – Gibt an, ob die einzelnen Aktionen zum Registrieren der DAC erfolgreich waren oder ob ein Fehler aufgetreten ist. Überprüfen Sie die Informationen, um zu bestimmen, ob die einzelnen Aktionen erfolgreich waren oder fehlgeschlagen sind. Für alle Aktionen, die fehlerhaft waren, ist in der Spalte **Ergebnis** ein Link enthalten. Klicken Sie auf den Link, um einen Bericht des für diese Aktion aufgetretenen Fehlers anzuzeigen.  
  
 **Bericht speichern** – Klicken Sie auf diese Schaltfläche, um den Registrierungsbericht in einer HTML-Datei zu speichern. In der Datei ist der Status der einzelnen Aktionen aufgeführt, einschließlich aller durch die Aktionen generierten Fehler. Der Standardordner ist ein Ordner **SQL Server Management Studio\DAC Packages** im Ordner „Dokumente“ unter Ihrem Windows-Konto. Der Dateiname hat das Format \<DACPackageName>_RegisterDACReport_yyyymmdd.html, wobei \<*DACPackageName*> dem Namen des bereitgestellten Pakets, *JJJJ* dem aktuellen Jahr, *MM* dem aktuellen Monat und *TT* dem aktuellen Tag entspricht.  
  
 **Fertig stellen** – Beendet den Assistenten.  
  
##  <a name="RegisterDACPowerShell"></a> Registrieren einer DAC mit PowerShell  
 **So registrieren Sie eine DAC mithilfe der Methode „Register()“ in einem PowerShell-Skript**  
  
1.  Erstellen Sie ein SMO-Serverobjekt, und legen Sie es auf die Instanz fest, die die als DAC zu registrierende Datenbank enthält.  
  
2.  Fügen Sie eine Variable hinzu, die den Namen der Datenbank angibt.  
  
3.  Geben Sie die Metadaten für die DAC an, z. B. DAC-Namen, Version und Beschreibung.  
  
4.  Führen Sie die Register-Methode mit den oben angegebenen Informationen aus.  
  
### <a name="example-powershell"></a>Beispiel (PowerShell)  
 Im folgenden Beispiel wird die Datenbank MyDB als DAC registriert.  
  
```  
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Specify the database to register as a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Register the DAC.  
$registerunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$registerunit.Description = $description  
$registerunit.Register()  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenebenenanwendungen](data-tier-applications.md)  
  
  
