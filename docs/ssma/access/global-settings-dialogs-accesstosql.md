---
title: Globale Einstellungen (Dialogfelder) (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 6c2204f2-d49e-49ba-9c0f-f14cf07fa561
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5b8ef85b9d0d997ed8aae05fc53aa685a2dcacfa
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67986407"
---
# <a name="global-settings-dialogs-accesstosql"></a>Globale Einstellungen (Dialogfelder) (accesstosql)
Auf der Seite Dialoge des Dialog Felds **globale Einstellungen** können Sie die Standardeinstellungen für Benutzeraktionen und Warnungen für SSMA festlegen.  
  
Um auf die Dialogfeld Einstellungen im **Menü Extras** zuzugreifen, klicken Sie auf **globale Einstellungen**, klicken Sie unten im linken Bereich auf **GUI** , und wählen Sie dann **Dialoge**aus.  
  
## <a name="options"></a>Optionen  
**Migrations-Assistenten beim Start anzeigen**  
In SSMA haben Sie die Möglichkeit, den **Migrations-Assistenten** beim Start der SSMA-Anwendung zu aktivieren oder zu deaktivieren. Diese Option ist standardmäßig auf **true**eingestellt.  
  
-   Wenn die Option auf **true**festgelegt ist, wird das Dialogfeld für den Migrations-Assistenten anfänglich angezeigt, wenn Sie SSMA für die Access-Anwendung öffnen.  
  
-   Wenn die Option auf **false**festgelegt ist, wird der Migrations-Assistent nicht angezeigt, und Sie müssen bei Bedarf manuell über das Menü **Datei** darauf zugreifen.  
  
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
  
