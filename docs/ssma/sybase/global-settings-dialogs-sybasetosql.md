---
title: Globale Einstellungen (Dialogfelder) (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e11452b7-ba94-4367-a745-5ccf1764acec
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 484460c56ae043561f8f19313e6f09743ba2caed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029082"
---
# <a name="global-settings-dialogs--sybasetosql"></a>Globale Einstellungen (Dialogfelder) (SybaseToSQL)
Mithilfe der Dialogfelder-Seite des der **globale Einstellungen** Dialogfeld zum Angeben der Standardaktion für Benutzer und die Einstellungen für die Warnung für SSMA.  
  
Um die Einstellungen des Dialogfelds auf die **Tools** , wählen Sie im Menü **globale Einstellungen**, klicken Sie auf **GUI** am unteren Rand der linken Seite, und wählen Sie dann **-Dialogfelder**.  
  
## <a name="options"></a>Optionen  
**Warnung vor dem Überschreiben von Objekten**  
Wenn SSMA Objekte in SQL Server konvertiert, möglicherweise einige Objekte in SQL Server-Metadaten des Projekts bereits vorhanden. Diese Objekte möglicherweise bereits konvertiert wurden, oder die Objekte möglicherweise einfach denselben Namen in das Zielschema als Objekte, die Sie konvertieren möchten.  
  
Verwenden Sie diese Option, um anzugeben, ob SSMA Sie auffordert, für das Überschreiben von doppelten Objektdefinitionen:  
  
-   Bei Auswahl von **"true"** , SSMA wird ein Warnungsdialogfeld angezeigt, wenn es sich um ein doppeltes Objekt trifft. In diesem Dialogfeld können Sie einzelne Objekte oder alle doppelten Objekte überschrieben, oder überspringen Sie einzelne Objekte oder alle doppelten Objekte angeben.  
  
-   Bei Auswahl von **"false"** , **Objekt überschreiben Standardaktion** Option wird angezeigt, in dem Sie die Standardaktion anzugeben.  
  
**Standardaktion des Objekts überschreiben**  
Diese Option wird angezeigt, wenn Sie die Option **"false"** für die **Warnung vor dem Überschreiben von Objekten** Option.  
  
Verwenden Sie diese Option, um anzugeben, das Standardobjekt Verhalten überschreiben:  
  
-   Bei Auswahl von **"true"** , SSMA werden Objekte in den Metadaten der SQL Server-Projekt, die den gleichen Namen aufweisen und das gleiche Ziel-Schema-Objekts, das konvertiert werden, automatisch überschrieben.  
  
-   Bei Auswahl von **"false"** , SSMA Metadaten des Objekts während der Konvertierung nicht überschrieben.  
  
