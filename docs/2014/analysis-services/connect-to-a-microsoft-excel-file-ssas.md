---
title: Herstellen einer Verbindung mit einer Microsoft Excel-Datei (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 48de9fd006c3918a23227a097743a95e138b577e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059034"
---
# <a name="connect-to-a-microsoft-excel-file-ssas"></a>Mit einer Microsoft Excel-Datei verbinden (SSAS)
  Auf dieser Seite des **Tabellenimport-Assistenten** können Sie eine Verbindung mit einer Microsoft Excel-Datei herstellen, die auf dem lokalen Computer gespeichert ist. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 Der entsprechende ACE-Anbieter muss auf dem Computer installiert sein, um eine Verbindung mit einer Microsoft Excel-Datei herzustellen. Weitere Informationen finden Sie unter [Unterstützte Datenquellen &#40;SSAS – tabellarisch&#41;](tabular-models/data-sources-supported-ssas-tabular.md).  
  
> [!NOTE]  
>  Beim Auswählen einer Datei auf dieser Seite werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Der Import ist jedoch nicht erfolgreich, wenn der auf der Seite Identitätswechselinformationen angegebene Benutzer nicht über ausreichend Berechtigungen zum Lesen aus der ausgewählten Datei verfügt.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Anzeigename der Verbindung**  
 Geben Sie einen eindeutigen Namen für diese Datenquellenverbindung ein. Dies ist ein Pflichtfeld.  
  
 **Excel-Dateipfad**  
 Geben Sie den vollständigen Pfad der Excel-Datei an.  
  
 **Durchsuchen**  
 Navigieren Sie zu einem Speicherort, an dem eine Excel-Datei verfügbar ist.  
  
 **Erweitert:**  
 Stellen Sie zusätzliche Verbindungseigenschaften im Dialogfeld **Erweiterte Eigenschaften festlegen** ein.  
  
 **Erste Zeile als Spaltenüberschriften verwenden**  
 Geben Sie an, ob die erste Datenzeile für die Spaltenüberschriften der Zieltabelle verwendet werden soll.  
  
 **Verbindung testen**  
 Stellen Sie unter Verwendung der aktuellen Einstellungen eine Verbindung mit der Datenquelle her. Eine Meldung gibt Aufschluss darüber, ob die Verbindungsherstellung erfolgreich war.  
  
  