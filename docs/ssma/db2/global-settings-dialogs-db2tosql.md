---
title: Globale Einstellungen (Dialogfelder) (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 360e01bb-6347-4e2b-acda-0daa161ed33b
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 10039fcd13a50a85b92b83598e17f1a821a14672
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87933761"
---
# <a name="global-settings-dialogs-db2tosql"></a>Globale Einstellungen (Dialogfelder) (DB2ToSQL)
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
  
