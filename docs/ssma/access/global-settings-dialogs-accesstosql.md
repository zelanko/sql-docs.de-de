---
title: Globale Einstellungen (Dialogfelder) (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 6c2204f2-d49e-49ba-9c0f-f14cf07fa561
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: dd1068e509a14c9d7388beea3727f2b30dd3ba40
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63299268"
---
# <a name="global-settings-dialogs-accesstosql"></a>Global Settings (Dialogs) (AccessToSQL)
Mithilfe der Dialogfelder-Seite des der **globale Einstellungen** Dialogfeld zum Angeben der Standardaktion für Benutzer und die Einstellungen für die Warnung für SSMA.  
  
Um die Einstellungen des Dialogfelds auf die **Tools** , wählen Sie im Menü **globale Einstellungen**, klicken Sie auf **GUI** am unteren Rand der linken Seite, und wählen Sie dann **-Dialogfelder**.  
  
## <a name="options"></a>Optionen  
**Migrations-Assistent beim Start anzeigen**  
In SSMA für Access, haben Sie eine Option zum Aktivieren oder deaktivieren Sie **Migrations-Assistent** beim Start der SSMA-Anwendung. Diese Option ist standardmäßig **"true"**.  
  
-   Wenn die Option, um festgelegt ist **"true"**, das Dialogfeld des Migrations-Assistenten sehen Sie Anfangs beim Öffnen von SSMA für Access-Anwendung.  
  
-   Wenn die Option, um festgelegt ist **"false"**, wird der Migrations-Assistent wird nicht angezeigt, und Sie müssen manuell aus den Zugriff auf die **Datei** Menü, falls erforderlich.  
  
**Warnung vor dem Überschreiben von Objekten**  
Wenn SSMA Objekte in SQL Server konvertiert, möglicherweise einige Objekte in SQL Server-Metadaten des Projekts bereits vorhanden. Diese Objekte möglicherweise bereits konvertiert wurden, oder die Objekte möglicherweise einfach denselben Namen in das Zielschema als Objekte, die Sie konvertieren möchten.  
  
Verwenden Sie diese Option, um anzugeben, ob SSMA Sie auffordert, für das Überschreiben von doppelten Objektdefinitionen:  
  
-   Bei Auswahl von **"true"**, SSMA wird ein Warnungsdialogfeld angezeigt, wenn es sich um ein doppeltes Objekt trifft. In diesem Dialogfeld können Sie einzelne Objekte oder alle doppelten Objekte überschrieben, oder überspringen Sie einzelne Objekte oder alle doppelten Objekte angeben.  
  
-   Bei Auswahl von **"false"**, **Objekt überschreiben Standardaktion** Option wird angezeigt, in dem Sie die Standardaktion anzugeben.  
  
**Standardaktion des Objekts überschreiben**  
Diese Option wird angezeigt, wenn Sie die Option **"false"** für die **Warnung vor dem Überschreiben von Objekten** Option.  
  
Verwenden Sie diese Option, um anzugeben, das Standardobjekt Verhalten überschreiben:  
  
-   Bei Auswahl von **"true"**, SSMA werden Objekte in den Metadaten der SQL Server-Projekt, die den gleichen Namen aufweisen und das gleiche Ziel-Schema-Objekts, das konvertiert werden, automatisch überschrieben.  
  
-   Bei Auswahl von **"false"**, SSMA Metadaten des Objekts während der Konvertierung nicht überschrieben.  
  
