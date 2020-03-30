---
title: Vorgang wird ausgeführt (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/11/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.performingoperation.f1
ms.assetid: 83259509-71d6-4a64-a7f2-4e9603b30bd4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 22f9918800930be9534441d2bb3706ad7844e9f7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "71285365"
---
# <a name="performing-operation-sql-server-import-and-export-wizard"></a>Vorgang wird ausgeführt (SQL Server-Import/Export-Assistent)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Nachdem Sie Ihre Auswahl im Assistenten überprüft und auf der Seite **Abschließen des Assistenten** auf **Fertig stellen** geklickt haben, zeigt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import/Export-Assistent **Vorgang wird ausgeführt**an. Auf dieser Seite sehen Sie den Status und das Ergebnis des Vorgangs, den Sie auf den vorherigen Seiten konfiguriert haben. Sie müssen auf dieser Seite keine Aktionen durchführen.

## <a name="screen-shot---operation-in-progress"></a>Screenshot: Vorgang wird ausgeführt 
 Der folgende Screenshot zeigt die Seite **Vorgang wird ausgeführt** des Assistenten während der Vorgang noch ausgeführt wird.  
  
 ![Seite „Vorgang wird ausgeführt“ im Import/Export-Assistenten](../../integration-services/import-export-data/media/performing-operation1.png "Seite „Vorgang wird ausgeführt“ im Import/Export-Assistenten")  

## <a name="screen-shot---operation-completed"></a>Screenshot: Vorgang wurde abgeschlossen 
 Der folgende Screenshot zeigt die Seite **Vorgang wird ausgeführt** des Assistenten nachdem der Vorgang abgeschlossen wurde. Klicken Sie auf ein Element in der Spalte **Nachricht** , um weitere Informationen zum jeweiligen Schritt zu erhalten.  
  
 ![Seite „Vorgang wird ausgeführt“ im Import/Export-Assistenten](../../integration-services/import-export-data/media/performing-operation2.png "Seite „Vorgang wird ausgeführt“ im Import/Export-Assistenten")  
  
## <a name="watch-the-progress-of-the-operation"></a>Überwachen des Vorgangsstatus
 **Aktion**  
 Zeigt jeden Schritt des Vorgangs an.  
  
 **Status**  
 Zeigt an, ob die einzelnen Schritte erfolgreich ausgeführt wurden oder fehlerhaft sind.  
  
 **Meldung**  
 Zeigt Informationen und Fehlermeldungen zu dem Schritt an. Klicken Sie auf ein Element in dieser Spalte, um weitere Informationen zum jeweiligen Schritt zu erhalten.

## <a name="interrupt-the-operation-or-save-the-results"></a>Unterbrechen des Vorgangs oder Speichern der Ergebnisse
 **Beenden**  
 Mit der Schaltfläche **Beenden** können Sie den Vorgang ggf. unterbrechen.  
  
 **Report**  
 Mit dieser Option können Sie einen Bericht mit den Ergebnissen anzeigen, den Bericht in einer Datei speichern, den Bericht in die Zwischenablage kopieren oder den Bericht per E-Mail versenden.  
  
## <a name="whats-next"></a>Wie geht es weiter?  
 Wenn der von Ihnen konfigurierte Vorgang ausgeführt und erfolgreich abgeschlossen wurde, sind Sie mit der Ausführung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Import/Export-Assistenten fertig.  
-   Wenn Sie den Vorgang sofort ausgeführt haben, können Sie das ausgewählte Ziel öffnen, um die Daten zu überprüfen, die der Assistent kopiert hat.  
-   Wenn Sie das vom Assistenten erstellte SSIS-Paket gespeichert haben, können Sie es in SQL Server Data Tools öffnen, um es anzupassen und wiederzuverwenden. Informationen zur Anpassung des gespeicherten Pakets und zur späteren erneuten Ausführung finden Sie unter [Speichern des SSIS-Pakets](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).

## <a name="see-also"></a>Weitere Informationen
[Erste Schritte mit diesem einfachen Beispiel des Import/Export-Assistenten](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)


