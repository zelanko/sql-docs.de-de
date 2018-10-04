---
title: Wählen Sie Tabellen und Sichten (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviews.f1
ms.assetid: 5e8121cc-03f0-4168-98cf-63c5c032bb0b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f341940849a1e3152048f8eea87ff946de4a02e2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092297"
---
# <a name="select-tables-and-views-ssas"></a>Tabellen und Sichten auswählen (SSAS)
  Auf dieser Seite des **Tabellenimport-Assistenten** können Sie die Tabellen und Sichten auswählen, aus denen Daten importiert werden sollen. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 Die Darstellung von Tabellen und Sichten auf dieser Seite garantiert nicht, dass der Import erfolgreich ist. Der Import ist nicht erfolgreich, wenn der auf der Seite Identitätswechselinformationen angegebene Benutzer nicht über ausreichend Berechtigungen zum Lesen aus der ausgewählten Datenbank verfügt.  
  
 Für Datenquellen mit Windows-Authentifizierung werden die Anmeldeinformationen des aktuellen Benutzers verwendet, um die Tabellen und die Sichten im Dialogfeld Tabellen und Sichten auswählen abzurufen. Für andere Datenquellen werden die in der Verbindungszeichenfolge angegebenen Anmeldeinformationen zum Abrufen der Daten verwendet.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Server**  
 Zeigt den Server an, mit dem Sie verbunden sind.  
  
 **Datenbank**  
 Zeigt die Datenbank an, die Sie ausgewählt haben.  
  
 **Tabellen und Sichten**  
 Führt die Tabellen und Sichten in der Datenbank auf. Aktivieren Sie das Kontrollkästchen neben jeder Tabelle und Sicht, die Sie importieren möchten.  
  
 **Quelltabelle**  
 Gibt den Namen der Quelltabelle auf Grundlage des Datenquellentyps an.  
  
 **Schema**  
 Gibt das Schema an, in dem die Quelltabelle enthalten ist. Je nach Typ der Datenbank funktioniert ein Schema als Container für andere Objekte, z. B. Tabellen, und kann auch den Besitzer dieser Objekte angeben.  
  
 **Anzeigename**  
 Gibt den benutzerfreundlichen Namen der Quelltabelle an. Standardmäßig zeigt die Spalte den Namen der Quelltabelle aus der Spalte **Quelltabelle** an. Ändern Sie den Namen, wenn Sie einen anderen als den in der Quelldatenbank verwendeten Namen verwenden möchten.  
  
 **Filterdetails**  
 Wenn ein Filter auf die importierten Daten angewendet wurde, wird der Datenimportfilter im Dialogfeld **Filterdetails** angezeigt. Weitere Informationen finden Sie unter [Filterdetails &#40;SSAS&#41;](filter-details-ssas.md).  
  
 **Vorschau und Filter**  
 Zeigt das Dialogfeld **Vorschau der ausgewählten Tabelle** an, das verwendet wird, um einen Filter auf die importierten Daten anzuwenden. Weitere Informationen finden Sie unter [Vorschau der ausgewählten Tabelle &#40;SSAS&#41;](preview-selected-table-ssas.md).  
  
 **Verknüpfte Tabellen auswählen**  
 Wählen Sie für den Import Tabellen und Sichten aus, die mit den Tabellen und Sichten verknüpft sind, die Sie bereits ausgewählt haben.  
  
  
