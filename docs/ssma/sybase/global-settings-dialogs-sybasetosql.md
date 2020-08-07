---
title: Globale Einstellungen (Dialogfelder) (sybasetosql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e11452b7-ba94-4367-a745-5ccf1764acec
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 4dc7bf9bf6b8f2e20fb8254a3a27ca2e293a0174
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87931461"
---
# <a name="global-settings-dialogs--sybasetosql"></a>Globale Einstellungen (Dialogfelder) (sybasetosql)
Auf der Seite Dialoge des Dialog Felds **globale Einstellungen** können Sie die Standardeinstellungen für Benutzeraktionen und Warnungen für SSMA festlegen.  
  
Um auf die Dialogfeld Einstellungen im **Menü Extras** zuzugreifen, klicken Sie auf **globale Einstellungen**, klicken Sie unten im linken Bereich auf **GUI** , und wählen Sie dann **Dialoge**aus.  
  
## <a name="options"></a>Optionen  
**Vor dem Überschreiben von Objekten warnen**  
Wenn SSMA Objekte in SQL Server konvertiert, sind einige Objekte möglicherweise bereits in den SQL Server Metadaten des Projekts vorhanden. Diese Objekte wurden möglicherweise bereits konvertiert, oder die Objekte können im Ziel Schema einfach denselben Namen haben wie Objekte, die Sie konvertieren möchten.  
  
Verwenden Sie diese Option, um anzugeben, ob Sie von SSMA aufgefordert werden sollen, doppelte Objekt Definitionen zu überschreiben:  
  
-   Wenn Sie " **true**" auswählen, zeigt SSMA ein Warn Dialogfeld an, wenn ein doppeltes Objekt gefunden wird. In diesem Dialogfeld können Sie angeben, dass einzelne Objekte oder alle doppelten Objekte überschrieben oder einzelne Objekte oder alle doppelten Objekte übersprungen werden sollen.  
  
-   Wenn Sie **false**auswählen, wird die Option **Objekt Standardaktion überschreiben** angezeigt, in der Sie die Standardaktion angeben.  
  
**Standardaktion zum Überschreiben von Objekten**  
Diese Option wird angezeigt, wenn Sie für die Option **Warnungen vor Überschreiben von Objekten** die Option **false** auswählen.  
  
Verwenden Sie diese Option, um das standardmäßige Objekt Überschreibungs Verhalten festzulegen:  
  
-   Wenn Sie **true**auswählen, werden Objekte in den SQL Server Projekt Metadaten, die denselben Namen aufweisen und sich im gleichen Ziel Schema wie das zu konvertierende Objekt befinden, von SSMA automatisch überschrieben.  
  
-   Wenn Sie **false**auswählen, werden Objekt Metadaten von SSMA während der Konvertierung nicht überschrieben.  
  
