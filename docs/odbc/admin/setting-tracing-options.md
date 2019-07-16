---
title: Festlegen von Ablaufverfolgungsoptionen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67901633"
---
# <a name="setting-tracing-options"></a>Festlegen von Ablaufverfolgungsoptionen
Die **Ablaufverfolgung** Registerkarte die **ODBC-Datenquellenadministrator** Dialogfeld können Sie so konfigurieren Sie die Möglichkeit, ODBC-Funktionsaufrufe werden nachverfolgt.  
  
## <a name="how-tracing-works"></a>Funktionsweise der Ablaufverfolgung  
 Wenn Sie die Ablaufverfolgung Starten der **Ablaufverfolgung** Registerkarte der Treiber-Manager protokolliert alle ODBC-Funktionsaufrufe für alle anschließend Ausführen von Anwendungen. ODBC-Funktionsaufrufe von Anwendungen, die ausgeführt werden, bevor die Ablaufverfolgung gestartet wird, werden nicht protokolliert. ODBC-Funktionsaufrufe werden in einer Protokolldatei aufgezeichnet, die Sie angeben.  
  
 Ablaufverfolgung angehalten, nur, nachdem Sie auf **Ablaufverfolgung jetzt beenden**. Denken Sie daran, dass während der Ablaufverfolgung wird die Protokolldatei nimmt weiter zu, und dies wirkt sich die Leistung von all Ihren ODBC-Anwendungen auf.  
  
 Weitere Informationen zur Ablaufverfolgung finden Sie unter [Ablaufverfolgung](../../odbc/reference/develop-app/tracing.md).  
  
### <a name="changes-in-odbc-tracing"></a>Änderungen in ODBC-Protokollierung  
 Vor dem MDAC 2.7 SP2 wurde ODBC-Protokollierung nur zulässig, auf einer computerweiten Basis erfolgen in der Ablaufverfolgung verfügbar gemachten Details zu allen ODBC-Anwendungen, die Identitäten unter aufzeichnet. Dazu gehörten die Ablaufverfolgung für ODBC-bezogene Aktivität, die auftreten kann, für Prozesse, die erstellt oder im Auftrag von anderen lokalen Benutzerkonten und Integrierte Sicherheitsprinzipale wie z. B. der lokale Dienst und Network Service ausgeführt.  
  
 In der Standardeinstellung werden ODBC-Ablaufverfolgung jetzt verwendet Einzelbenutzer-Modus. Wenn Sie ein lokaler Administrator sind, können jedoch Sie weiterhin eine computerweite Ablaufverfolgung aktivieren mithilfe von ODBC-Datenquellen-Administrator.  
  
 So konfigurieren Sie den ODBC-Ablaufverfolgung-Modus:  
  
1.  Wenn es erforderlich ist, melden Sie sich mit einem Konto, das Mitglied der lokalen Administratorengruppe ist.  
  
2.  Öffnen Sie aus der Verwaltung der ODBC-Datenquellen-Administrator.  
  
3.  Klicken Sie auf die **Ablaufverfolgung** Registerkarte.  
  
4.  Konfigurieren Sie die Ablaufverfolgung Modus gemäß der **computerweite-Ablaufverfolgung für alle Benutzeridentitäten** Kontrollkästchen:  
  
5.  Aktivieren Sie das Kontrollkästchen zum Aktivieren der Ablaufverfolgung für computerweite.  
  
6.  Deaktivieren Sie das Kontrollkästchen, damit wieder der Einzelbenutzer-Ablaufverfolgung.  
  
7.  Klicken Sie auf **Übernehmen**.  
  
> [!NOTE]  
>  Wenn die Ablaufverfolgung bereits in einem Modus gestartet haben, müssen Sie die Ablaufverfolgung zu beenden, und wechseln Sie zu den jeweils anderen Modus für den Modus wurde erfolgreich geändert werden.  
  
> [!IMPORTANT]  
>  Computerweite Ablaufverfolgung sollte nur aktiviert werden, wenn er benötigt wird; Andernfalls sollte bleiben werden deaktiviert.  
  
## <a name="visual-studio-analyzer-tracing"></a>Visual Studio Analyzer-Ablaufverfolgung  
  
> [!IMPORTANT]  
>  Unterstützung für Visual Studio Analyzer wurde ab Windows 8 (Visual Studio Analyzer wurde nur in früheren Versionen von Visual Studio enthalten.) entfernt. Verwenden Sie eine Alternative zur Problembehandlung Mechanismus BID-Verfolgung.  
  
 Visual Studio® Analyzer-Ablaufverfolgung bietet, Leistung und Debuginformationen über die ODBC-Ebene. Aller ausgehenden Ereignisse werden auf Schnittstellenebene genauen ein Bild dargestellt in ODBC-Komponenten in Bezug auf Zeit verbracht, wie möglich auf oberster Ebene ausgelöst. Visual Studio Analyzer-Ablaufverfolgung, erfordert jede Ereignisquelle zu registrieren, wenn die Quelle eingerichtet wird. Weitere Informationen über diese Art der Ablaufverfolgung finden Sie in Visual Studio-Dokumentation.
