---
title: Interaktiver Microsoft-Replikationskonfliktlöser | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.interactiveresolver.f1
ms.assetid: d3d4a480-782b-4b1d-b839-565c8cf6cb24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 68ddc4f6b42dcc53445b8afaae0bc15e666a5711
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62667282"
---
# <a name="microsoft-replication-interactive-conflict-resolver"></a>Interaktiver Microsoft-Replikationskonfliktlöser
  Der interaktive Replikationskonfliktlöser kann für Mergeabonnements verwendet werden, die mithilfe der Synchronisierungsverwaltung von Windows synchronisiert werden. Er ermöglicht es Ihnen, das Ergebnis von Datenkonflikten anzuzeigen, zu vergleichen, zu bearbeiten und auszuwählen. Die Replikation beinhaltet auch den Konflikt-Viewer, der es Ihnen ermöglicht, die Ergebnisse von Konflikten anzuzeigen und zu ändern, nachdem für sie ein Commit ausgeführt wurde. Mithilfe des interaktiven Konfliktlösers können Sie das Ergebnis während der Synchronisierung auswählen.  
  
> [!NOTE]  
>  Konflikte im Zusammenhang mit logischen Datensätzen werden nicht im interaktiven Konfliktlöser angezeigt. Mit den gespeicherten Replikationsprozeduren können Informationen zu diesen Konflikten angezeigt werden. Weitere Informationen finden Sie unter [Anzeigen von Konfliktinformationen zu Mergeveröffentlichungen &#40;Replikationsprogrammierung mit Transact-SQL&#41;](view-conflict-information-for-merge-publications.md)  
  
## <a name="options"></a>Optionen  
 **Spaltenname**  
 Der Name aller Spalten in der Tabelle Die Daten einer oder mehrerer Spalten können Konflikte verursachen. Unabhängig davon, zwischen welchen Spalten es zu Konflikten kommt, überschreibt die gesamte gewinnende Zeile die gesamte verlierende Zeile.  
  
 **Vorgeschlagene Lösung**  
 Die vom Konfliktlöser für den Artikel vorgeschlagene Lösung.  
  
 **Verleger**  
 Der Datenwert auf dem Verleger.  
  
 **Abonnent**  
 Der Datenwert auf dem Abonnenten.  
  
 **Vorschläge akzeptieren**, **Verleger akzeptieren**und **Abonnenten akzeptieren**  
 Klicken Sie, je nachdem wer den Konflikt verloren hat, entweder auf Abonnent oder Verleger, um die anzuwendende Zeile anzunehmen. Wenn der Verleger den Konflikt verloren hat, empfangen alle anderen Abonnenten bei der nächsten Synchronisierung mit dem Verleger die gewinnende Zeile.  
  
 **Verbleibende Konflikte automatisch lösen**  
 Lösen Sie alle verbleibenden Konflikte anhand der für den Artikel vom Konfliktlöser vorgeschlagenen Lösung.  
  
 **Details dieses Konflikts zur späteren Bezugnahme protokollieren**  
 Protokollieren Sie die Details des Konflikts in Systemtabellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Interaktive Konfliktlösung](merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [Anzeigen und Lösen von Datenkonflikten für Mergeveröffentlichungen &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)   
 [Synchronisieren eines Abonnements mithilfe der Synchronisierungsverwaltung von Windows &#40;Synchronisierungsverwaltung von Windows&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md)   
 [Advanced Merge Replication Conflict Detection and Resolution (Erweiterte Konflikterkennung und -lösung bei der Mergereplikation)](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
