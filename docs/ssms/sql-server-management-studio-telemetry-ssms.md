---
title: SQL Server Management Studio – Telemetrie (SSMS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/20/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ce4abde855b5fe6a65c3038e93eb8609f9736dc1
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2019
ms.locfileid: "59240388"
---
# <a name="local-audit-for-ssms-usage-and-diagnostic-data-collection"></a>Lokale Überwachung für SSMS-Nutzungs- und -Diagnosedatensammlung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SQL Server Management Studio (SSMS) enthält internetfähige Features, die anonyme Featurenutzungs- und Diagnosedaten sammeln und an Microsoft senden können. SSMS erfasst möglicherweise Standardinformationen zu Ihrem Computer und Informationen zur Nutzung und Leistung, die möglicherweise an Microsoft übermittelt und analysiert werden, um die Qualität, Sicherheit und Zuverlässigkeit von SSMS zu optimieren. Wir erfassen nicht Ihren Namen, Ihre Adresse oder andere Kontaktinformationen. Ausführliche Informationen finden Sie in den [Datenschutzbestimmungen von Microsoft](https://privacy.microsoft.com/privacystatement) und den [Ergänzenden Datenschutzbestimmungen zu SQL Server](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="audit-feature-usage-data"></a>Überwachen von Featurenutzungsdaten

Machen Sie Folgendes, um sich die von SSMS erfassten Featurenutzungsdaten anzeigen zu lassen:
1.  Starten Sie SSMS.
2.  Klicken Sie auf **View** (Ansicht), und klicken Sie anschließend im Hauptmenü auf **Output** (Ausgabe), um das Fenster **Output** (Ausgabe) anzuzeigen. 
3.  Wenn das Fenster **Output** (Ausgabe) angezeigt wird, wählen Sie im Menü **Show output from:** (Ausgabe anzeigen von:) **Telemetry** (Telemetrie) aus.

Während Sie SSMS verwenden, um mit Ihrer Datenbank zu interagieren, zeigt das Fenster **Output** (Ausgabe) die erfassten Daten an.

## <a name="enable-or-disable-usage-feedback-collection-in-ssms"></a>Feedbackerfassung der Nutzung in SSMS aktivieren bzw. deaktivieren

So aktivieren oder deaktivieren Sie die Sammlung von Nutzungsdaten für SSMS

- Für SQL Server Management Studio 17:

  `Subkey = HKEY_CURRENT_USER\Software\Microsoft\SQL Server Management Studio\14.0`

  RegEntry name = `UserFeedbackOptIn`

  Eintragstyp `DWORD`: `0` steht für Deaktivieren und `1` für Aktivieren.

  Außerdem basiert SSMS 17.x auf der Visual Studio 2015-Shell, und die Visual Studio-Installation ermöglicht standardmäßig Kundenfeedback.  

  Um Visual Studio so zu konfigurieren, dass Kundenfeedback auf einzelnen Computern deaktiviert ist, ändern Sie den Wert des folgenden Registrierungsunterschlüssels in die Zeichenfolge `0`: `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM OptIn`

  Beispiel: Ändern Sie den Unterschlüssel wie folgt:  
  `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM OptIn `=` 0`

  Die registrierungsbasierte Gruppenrichtlinie dieser Registrierungsschlüssel wird von der Nutzungs- und Diagnosedatenerfassung von SQL Server 2017 berücksichtigt.

- Für SQL Server Management Studio 18:

  `Subkey = HKEY_CURRENT_USER\Software\Microsoft\SQL Server Management Studio\18.0_IsoShell`

  RegEntry name = `UserFeedbackOptIn`

  Eintragstyp `DWORD`: `0` steht für Deaktivieren und `1` für Aktivieren.

## <a name="see-also"></a>Weitere Informationen

- [Konfigurieren der Nutzungs- und Diagnosedatensammlung für SQL Server](../sql-server/usage-and-diagnostic-data-configuration-for-sql-server.md)
- [Lokale Überwachung für SQL Server-Nutzungs- und -Diagnosedatensammlung](http://msdn.microsoft.com/library/mt743085.aspx)
