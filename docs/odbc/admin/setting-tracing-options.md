---
title: Festlegen von Ablauf Verfolgungs Optionen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 13e8caf9f3a9643f8063d6227258245a603f1665
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67901633"
---
# <a name="setting-tracing-options"></a>Festlegen von Ablaufverfolgungsoptionen
Mithilfe der Registerkarte Ablauf **Verfolgung** des Dialog Felds **ODBC-Datenquellen-Administrator** können Sie konfigurieren, wie ODBC-Funktionsaufrufe verfolgt werden.  
  
## <a name="how-tracing-works"></a>Funktionsweise der Ablauf Verfolgung  
 Wenn Sie die Ablauf Verfolgung über die Registerkarte Ablauf **Verfolgung** starten, protokolliert der Treiber-Manager alle ODBC-Funktionsaufrufe für alle anschließenden Anwendungen. ODBC-Funktionsaufrufe von Anwendungen, die vor dem Start der Ablauf Verfolgung ausgeführt werden, werden nicht protokolliert. ODBC-Funktionsaufrufe werden in einer von Ihnen angegebenen Protokolldatei aufgezeichnet.  
  
 Die Ablauf Verfolgung wird erst beendet, wenn Sie auf Ablauf **Verfolgung beenden**klicken. Beachten Sie, dass die Protokolldatei während der Ablauf Verfolgung weiterhin zunimmt und dies die Leistung aller ODBC-Anwendungen beeinträchtigt.  
  
 Weitere Informationen zur Ablauf Verfolgung finden Sie unter Ablauf [Verfolgung](../../odbc/reference/develop-app/tracing.md).  
  
### <a name="changes-in-odbc-tracing"></a>Änderungen in der ODBC-Ablauf Verfolgung  
 Vor MDAC 2,7 SP2 konnte die ODBC-Ablauf Verfolgung nur auf Computer Ebene ausgeführt werden, bei der die Ablauf Verfolgung Details zu allen ODBC-Anwendungen bereitstellt, die unter allen Identitäten ausgeführt werden. Dies umfasste die Ablauf Verfolgung für ODBC-bezogene Aktivitäten, die bei Prozessen auftreten können, die für andere lokale Benutzerkonten erstellt oder ausgeführt wurden, sowie integrierte Sicherheits Prinzipale wie der lokale Dienst und der Netzwerkdienst.  
  
 Standardmäßig verwendet die ODBC-Ablauf Verfolgung jetzt den Einzelbenutzermodus. Wenn Sie ein lokaler Administrator sind, können Sie die Computer weite Ablauf Verfolgung jedoch weiterhin mit dem ODBC-Datenquellen-Administrator aktivieren.  
  
 So konfigurieren Sie den ODBC-Ablauf Verfolgungs Modus:  
  
1.  Wenn dies erforderlich ist, melden Sie sich mit einem Konto an, das Mitglied der lokalen Administratoren Gruppe ist.  
  
2.  Öffnen Sie unter "Verwaltung" den ODBC-Datenquellen-Administrator.  
  
3.  Klicken auf die Registerkarte Ablauf **Verfolgung** .  
  
4.  Konfigurieren Sie den Ablauf Verfolgungs Modus mithilfe des Kontrollkästchens **Computer weite Ablauf Verfolgung für alle Benutzer Identitäten** :  
  
5.  Aktivieren Sie das Kontrollkästchen, um die Computer weite Ablauf Verfolgung zu aktivieren.  
  
6.  Deaktivieren Sie das Kontrollkästchen, um zur Ablauf Verfolgung pro Benutzer zurückzukehren.  
  
7.  Klicken Sie auf **Anwenden**.  
  
> [!NOTE]  
>  Wenn Sie die Ablauf Verfolgung bereits in einem Modus gestartet haben, müssen Sie die Ablauf Verfolgung abbrechen und in den anderen Modus wechseln, damit der Modus erfolgreich geändert wird.  
  
> [!IMPORTANT]  
>  Die Computer weite Ablauf Verfolgung sollte nur aktiviert werden, wenn Sie benötigt wird. Andernfalls sollte Sie deaktiviert bleiben.  
  
## <a name="visual-studio-analyzer-tracing"></a>Visual Studio Analyzer Ablauf Verfolgung  
  
> [!IMPORTANT]  
>  Die Unterstützung für Visual Studio Analyzer wurde ab Windows 8 entfernt (Visual Studio Analyzer war nur in früheren Versionen von Visual Studio enthalten.) Verwenden Sie für einen alternativen Mechanismus zur Problembehandlung die Auftrags Ablauf Verfolgung.  
  
 Die Visual Studio® Analyzer-Ablauf Verfolgung bietet Informationen zur Leistung und zum Debuggen der ODBC-Schicht. Alle ausgehenden Ereignisse werden auf der Oberfläche der obersten Ebene ausgelöst, sodass Sie so genau wie möglich in Bezug auf die in den ODBC-Komponenten aufgewendeten Zeit vorhanden sind. Visual Studio Analyzer Ablauf Verfolgung erfordert die Registrierung einer beliebigen Ereignis Quelle, wenn die Quelle eingerichtet ist. Weitere Informationen zu dieser Art der Ablauf Verfolgung finden Sie in der Visual Studio-Dokumentation.
