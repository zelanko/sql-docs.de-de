---
title: Festlegen von Ablaufverfolgungsoptionen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Analyzer tracing [ODBC]
- ODBC data source administrator [ODBC], tracing options
- tracing options [ODBC], ODBC data source administrator
ms.assetid: 44404a79-b716-4bc1-9ffb-70cd8239d237
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 21bee5d903459423a134389e62db844f5f63c9c1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307196"
---
# <a name="setting-tracing-options"></a>Festlegen von Ablaufverfolgungsoptionen
Auf der Registerkarte **Ablaufverfolgung** des Dialogfelds **ODBC Data Source Administrator** können Sie konfigurieren, wie ODBC-Funktionsaufrufe verfolgt werden.  
  
## <a name="how-tracing-works"></a>Funktionsweise der Ablaufverfolgung  
 Wenn Sie die Ablaufverfolgung über die Registerkarte **Ablaufverfolgung** starten, protokolliert der Treiber-Manager alle ODBC-Funktionsaufrufe für alle nachträglich ausgeführten Anwendungen. ODBC-Funktionsaufrufe von Anwendungen, die ausgeführt werden, bevor die Ablaufverfolgung gestartet wird, werden nicht protokolliert. ODBC-Funktionsaufrufe werden in einer von Ihnen angegebenen Protokolldatei aufgezeichnet.  
  
 Die Ablaufverfolgung wird erst beendet, nachdem Sie auf **Ablaufverfolgung jetzt beenden**geklickt haben. Denken Sie daran, dass die Protokollierung während der Folgenden-Protokollierung weiter zunimmt und sich dies auf die Leistung aller ODBC-Anwendungen auswirkt.  
  
 Weitere Informationen zur Ablaufverfolgung finden Sie unter [Ablaufverfolgung](../../odbc/reference/develop-app/tracing.md).  
  
### <a name="changes-in-odbc-tracing"></a>Änderungen in der ODBC-Ablaufverfolgung  
 Vor MDAC 2.7 SP2 durfte die ODBC-Ablaufverfolgung nur maschinenweit erfolgen, bei dem Trace-Captures offengelegte Details zu allen ODBC-Anwendungen erfassen, die unter beliebigen Identitäten ausgeführt werden. Dies umfasste die Ablaufverfolgung von ODBC-bezogenen Aktivitäten, die für Prozesse auftreten können, die im Auftrag anderer lokaler Benutzerkonten erstellt oder ausgeführt werden, und integrierte Sicherheitsprinzipale wie den lokalen Dienst und den Netzwerkdienst.  
  
 Standardmäßig verwendet die ODBC-Ablaufverfolgung jetzt den Benutzermodus. Wenn Sie jedoch ein lokaler Administrator sind, können Sie die maschinenweite Ablaufverfolgung weiterhin mithilfe des ODBC-Datenquellenadministrators aktivieren.  
  
 So konfigurieren Sie den ODBC-Ablaufverfolgungsmodus:  
  
1.  Melden Sie sich ggf. mit einem Konto an, das mitglied in der Gruppe Lokale Administratoren ist.  
  
2.  Öffnen Sie unter Administrative Tools den ODBC-Datenquellenadministrator.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufverfolgung.**  
  
4.  Konfigurieren Sie den Ablaufverfolgungsmodus mithilfe des **Kontrollkästchens Machine-Wide-Ablaufverfolgung für alle Benutzeridentitäten:**  
  
5.  Um die maschinenweite Ablaufverfolgung zu aktivieren, aktivieren Sie das Kontrollkästchen.  
  
6.  Um zur Ablaufverfolgung pro Benutzer zurückzukehren, deaktivieren Sie das Kontrollkästchen.  
  
7.  Klicken Sie auf **Anwenden**.  
  
> [!NOTE]  
>  Wenn Sie die Ablaufverfolgung bereits in einem Modus gestartet haben, müssen Sie die Ablaufverfolgung beenden und in den anderen Modus wechseln, damit der Modus erfolgreich geändert werden kann.  
  
> [!IMPORTANT]  
>  Die maschinenweite Ablaufverfolgung sollte nur dann aktiviert werden, wenn sie benötigt wird. Andernfalls sollte es deaktiviert werden.  
  
## <a name="visual-studio-analyzer-tracing"></a>Visual Studio Analyzer-Ablaufverfolgung  
  
> [!IMPORTANT]  
>  Die Unterstützung für Visual Studio Analyzer wurde ab Windows 8 entfernt (Visual Studio Analyzer war nur in älteren Versionen von Visual Studio enthalten). Verwenden Sie für einen alternativen Fehlerbehebungsmechanismus die BID-Ablaufverfolgung.  
  
 Visual Studio® Analyzer Tracing bietet Leistungs- und Debuginformationen zum ODBC-Layer. Alle ausgehenden Ereignisse werden an der Schnittstelle der obersten Ebene ausgelöst, um ein möglichst genaues Bild über die in ODBC-Komponenten verbrachte Zeit zu erhalten. Visual Studio Analyzer Tracing erfordert, dass sich eine Ereignisquelle registriert, wenn die Quelle eingerichtet ist. Weitere Informationen zu dieser Art der Ablaufverfolgung finden Sie in der Visual Studio-Dokumentation.
