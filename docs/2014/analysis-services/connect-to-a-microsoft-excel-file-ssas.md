---
title: Herstellen einer Verbindung mit einer Microsoft Excel-Datei (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e49b37a6f344b7fc6c45c9767a05c7f7d5bfe6e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087322"
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
  
 **Erweitert**  
 Legen Sie zusätzliche Verbindungs Eigenschaften im Dialogfeld **Erweiterte Eigenschaften festlegen** fest.  
  
 **Erste Zeile als Spaltenüberschriften verwenden**  
 Geben Sie an, ob die erste Datenzeile für die Spaltenüberschriften der Zieltabelle verwendet werden soll.  
  
 **Verbindung testen**  
 Stellen Sie unter Verwendung der aktuellen Einstellungen eine Verbindung mit der Datenquelle her. Eine Meldung gibt Aufschluss darüber, ob die Verbindungsherstellung erfolgreich war.  
  
  
