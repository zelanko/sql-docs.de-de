---
title: Aktivieren oder Deaktivieren von remote R-paketverwaltung – SQL Server Machine Learning Services
description: Aktivieren von remote R-paketverwaltung für SQL Server 2016 R Services oder SQL Server 2017-Machine Learning Services (Datenbankintern)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: ee52fd9b7a116156f794303b828a83e9b06de6ab
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509817"
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Aktivieren Sie oder deaktivieren Sie der remote-paketverwaltung für SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt, wie Sie die Remoteverwaltung der R-Pakete von einer Clientarbeitsstation oder einem anderen Machine Learning-Server zu aktivieren. Nachdem die paketverwaltungsfunktion auf SQL Server aktiviert wurde, können Sie RevoScaleR-Befehle auf einem Client verwenden, um Pakete auf SQL Server zu installieren.

> [!NOTE]
> Derzeit wird die Verwaltung von R-Bibliotheken unterstützt. die Unterstützung für Python in der Roadmap enthalten ist.

Standardmäßig ist die externe paketverwaltungsfunktion für SQL Server deaktiviert. Sie müssen ein separates Skript zum Aktivieren des Features, wie im nächsten Abschnitt beschrieben ausführen.

## <a name="overview-of-process-and-tools"></a>Übersicht über die Verfahren und tools

Zum Aktivieren oder Deaktivieren der paketverwaltung für SQL Server, verwenden Sie das Befehlszeile-Hilfsprogramm **RegisterRExt.exe**, das ist im Lieferumfang der **RevoScaleR** Paket.

[Aktivieren der](#bkmk_enable) dieses Feature ist ein zweistufiger Prozess, erfordert einen Datenbankadministrator: Sie Aktivieren der paketverwaltung für SQL Server-Instanz (je einmal pro SQL Server-Instanz), und klicken Sie dann Aktivieren der paketverwaltung für SQL-Datenbank (je einmal pro SQL Server -Datenbank).

[Deaktivieren von](#bkmk_disable) die paketverwaltungsfunktion ist auch die Multipel Schritte erforderlich: Sie entfernen auf Datenbankebene Pakete und Berechtigungen (einmal pro Datenbank), und entfernen Sie die Rollen vom Server (je einmal pro Instanz).

## <a name="bkmk_enable"></a> Aktivieren der paketverwaltung

1. Öffnen Sie auf SQL Server eine Eingabeaufforderung mit erhöhten Rechten, und navigieren Sie zu dem Ordner mit dem Hilfsprogramm RegisterRExt.exe. Der Standardspeicherort ist `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Führen Sie den folgenden Befehl, der entsprechenden Argumente für Ihre Umgebung bereitstellen:

    `RegisterRExt.exe /install pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Dieser Befehl erstellt die-Objekte auf Instanzebene auf dem SQL Server-Computer, die für die paketverwaltung erforderlich sind. Diese neu gestartet, wird des LaunchPads für die Instanz.

    Wenn Sie eine Instanz nicht angeben, wird die Standardinstanz verwendet. Wenn Sie einen Benutzer nicht angeben, wird der aktuelle Sicherheitskontext verwendet. So ermöglicht z. B. der folgende Befehl paketverwaltung für die Instanz im Pfad RegisterRExt.exe, mit den Anmeldeinformationen des Benutzers, der die Eingabeaufforderung geöffnet:

    `REgisterRExt.exe /install pkgmgmt`

3. Um paketverwaltung auf eine bestimmte Datenbank hinzuzufügen, führen Sie den folgenden Befehl an einer Eingabeaufforderung mit erhöhten Rechten aus:

    `RegisterRExt.exe /install pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Dieser Befehl erstellt einige datenbankartefakte, einschließlich der folgenden Datenbankrollen, die verwendet werden, zum Steuern von Benutzerberechtigungen: `rpkgs-users`, `rpkgs-private`, und `rpkgs-shared`.

    Zum Beispiel ermöglicht der folgende Befehl paketverwaltung in der Datenbank, für die Instanz, die dem RegisterRExt ausgeführt wird. Wenn Sie einen Benutzer nicht angeben, wird der aktuelle Sicherheitskontext verwendet.

    `RegisterRExt.exe /install pkgmgmt /database:TestDB`

4. Wiederholen Sie den Befehl für jede Datenbank, in dem Pakete installiert werden müssen.

5. Um sicherzustellen, dass der neuen Rollen erstellt wurden, klicken Sie in SQL Server Management Studio, auf die Datenbank, erweitern Sie **Sicherheit**, und erweitern Sie **Datenbankrollen**.

    Sie können auch eine Abfrage auf Sys. database_principals, z. B. Folgendes ausführen:

    ```sql
    SELECT pr.principal_id, pr.name, pr.type_desc,   
        pr.authentication_type_desc, pe.state_desc,   
        pe.permission_name, s.name + '.' + o.name AS ObjectName  
    FROM sys.database_principals AS pr  
    JOIN sys.database_permissions AS pe  
        ON pe.grantee_principal_id = pr.principal_id  
    JOIN sys.objects AS o  
        ON pe.major_id = o.object_id  
    JOIN sys.schemas AS s  
        ON o.schema_id = s.schema_id;
    ```

Nachdem Sie dieses Feature aktiviert haben, können Sie die RevoScaleR-Funktion verwenden, installieren oder Deinstallieren von Paketen von einem Remoteclient von R.

## <a name="bkmk_disable"></a> Deaktivieren der paketverwaltung

1. Eine Eingabeaufforderung mit erhöhten Rechten führen Sie das Hilfsprogramm RegisterRExt erneut aus, und deaktivieren Sie der paketverwaltung auf Datenbankebene:

    `RegisterRExt.exe /uninstall pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Dieser Befehl entfernt die Datenbankobjekte, die im Zusammenhang mit der Verwaltung von Paketen aus der angegebenen Datenbank. Es entfernt auch alle Pakete, die von der geschützten Speicherort im Dateisystem auf dem SQL Server-Computer installiert wurden.

2. Wiederholen Sie diesen Befehl für jede Datenbank, für die paketverwaltung verwendet wurde.

3.  (Optional) Nachdem alle Datenbanken der Pakete, die mit dem vorherigen Schritt gelöscht worden sind, führen Sie den folgenden Befehl an einer Eingabeaufforderung mit erhöhten Rechten aus:

    `RegisterRExt.exe /uninstall pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Dieser Befehl entfernt die paketverwaltungsfunktion aus der Instanz an. Sie müssen möglicherweise den Launchpad-Dienst, um Änderungen zu sehen, manuell neu zu starten.

## <a name="next-steps"></a>Nächste Schritte

+ [Verwenden von RevoScaleR zum Installieren neuer R-Pakete](use-revoscaler-to-manage-r-packages.md)
+ [Tipps für die Installation von R-Pakete](packages-installed-in-user-libraries.md)
+ [Standardpakete](installing-and-managing-r-packages.md)
