---
title: Tabellen und Sichten auswählen (Daten Feeds) (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviewsdf.f1
ms.assetid: 6c4fafe0-e02e-47d1-b8bc-e70e872690af
author: minewiskan
ms.author: owend
ms.openlocfilehash: d57966a414ec3b332334a4357c15425e8215df14
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940831"
---
# <a name="select-tables-and-views-data-feeds-ssas"></a>Tabellen und Sichten auswählen (Datenfeeds) (SSAS)
  Auf dieser Seite des **Tabellenimport-Assistenten** können Sie die Tabellen und Sichten auswählen, aus denen Daten importiert werden sollen. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 Die Darstellung von Tabellen und Sichten auf dieser Seite garantiert nicht, dass der Import erfolgreich ist. Der Import ist nicht erfolgreich, wenn der auf der Seite Identitätswechselinformationen angegebene Benutzer nicht über ausreichend Berechtigungen zum Lesen aus der ausgewählten Datenbank verfügt.  
  
 Für Datenquellen mit Windows-Authentifizierung werden die Anmeldeinformationen des aktuellen Benutzers verwendet, um die Tabellen und die Sichten im Dialogfeld Tabellen und Sichten auswählen abzurufen. Für andere Datenquellen werden die in der Verbindungszeichenfolge angegebenen Anmeldeinformationen zum Abrufen der Daten verwendet.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
 **Datenfeed-URL**  
 Zeigt die URL für den Datenfeed an, den Sie ausgewählt haben.  
  
 **Tabellen und Sichten**  
 Führt die Tabellen und Sichten im Datenfeed auf. Aktivieren Sie das Kontrollkästchen neben jeder Tabelle und Sicht, die Sie importieren möchten.  
  
 **Quell Tabelle**  
 Gibt den Namen der Quelltabelle auf Grundlage des Datenquellentyps an.  
  
 **Anzeigename**  
 Gibt den benutzerfreundlichen Namen der Quelltabelle an. Standardmäßig zeigt die Spalte den Namen der Quelltabelle aus der Spalte **Quelltabelle** an.  
  
 **Filterdetails**  
 Wenn ein Filter auf die importierten Daten angewendet wurde, wird der Datenimportfilter im Dialogfeld **Filterdetails** angezeigt. Weitere Informationen finden Sie unter [Filterdetails &#40;SSAS&#41;](filter-details-ssas.md).  
  
 **Vorschau anzeigen und filtern**  
 Zeigt das Dialogfeld **Vorschau der ausgewählten Tabelle** an, das verwendet wird, um einen Filter auf die importierten Daten anzuwenden. Weitere Informationen finden Sie unter [Vorschau der ausgewählten Tabelle &#40;SSAS&#41;](preview-selected-table-ssas.md).  
  
 **Verknüpfte Tabellen auswählen**  
 Wählen Sie Tabellen aus, die mit den Tabellen und Sichten verknüpft sind, die Sie ausgewählt haben.  
  
  
