---
title: Öffnen einer Vorlage
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dd59b435c1c0fbd3461333305824aca61c68d296
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75245692"
---
# <a name="open-a-template"></a>Öffnen einer Vorlage
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Sie können eine Vorlage über den Vorlagen-Explorer öffnen.  
  
## <a name="to-open-a-template-from-template-explorer"></a>So öffnen Sie eine Vorlage über den Vorlagen-Explorer  
Vorlagen lassen sich über den Vorlagen-Explorer öffnen.  
  
1.  Klicken Sie zum Öffnen des Vorlagen-Explorers im Menü **Ansicht** auf **Vorlagen-Explorer**.  
  
2.  Erweitern Sie in der Liste mit Vorlagenkategorien die Kategorie mit der zu öffnenden Vorlage.  
  
3.  Die Vorlage lässt sich anhand von drei Methoden öffnen:  
  
    1.  Doppelklicken Sie auf die Vorlage, um sie in einem Code-Editor-Fenster zu öffnen.  
  
    2.  Klicken Sie mit der rechten Maustaste auf die Vorlage, und wählen Sie **Öffnen** aus, um die Vorlage in einem Code-Editor-Fenster zu öffnen.  
  
    3.  Ziehen Sie die Vorlage in ein Code-Editor-Fenster, um dem Inhalt des Editor-Fensters den Vorlagencode hinzuzufügen.  
  
Sobald die Vorlage geöffnet ist, können Sie im Dialogfeld **Vorlagenparameter ersetzen** die Parameter in der Vorlage durch Ihre eigenen Werte ersetzen.  
  
Wird durch das Öffnen einer Vorlage ein neues Editor-Fenster geöffnet, erfolgt dies mit den Anmeldeinformationen der aktuellen aktiven Verbindung. Ist beispielsweise beim Öffnen einer CREATE DATABASE-Vorlage eine [!INCLUDE[ssDE](../../includes/ssde_md.md)] -Instanz im Objekt-Explorer fokussiert, wird ein neues Editor-Fenster mit einer Verbindung zu dieser Instanz geöffnet. Ist keine aktive Verbindung vorhanden, gibt [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ein Anmeldedialogfeld zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
[Template Explorer](../../ssms/template/template-explorer.md)  
[Vorlagenparameter ersetzen](../../ssms/template/replace-template-parameters.md)  
  
