---
title: Verbinden mit Microsoft SQL Server Analysis Services (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserveras.f1
ms.assetid: 7f3244ee-b690-471c-893d-68e361c2d416
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 350251b6813027455f8e1e9b83dcf2508371df70
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129850"
---
# <a name="connect-to-microsoft-sql-server-analysis-services-ssas"></a>Verbindung mit Microsoft SQL Server Analysis Services herstellen (SSAS)
  Auf dieser Seite des der **Tabellenimport-Assistenten** ermöglicht Ihnen die Angabe von Einstellungen für das Importieren von Daten aus einem Microsoft SQL Server Analysis Services-Cube oder einer PowerPivot-Arbeitsmappe, die in SharePoint gehostet wird. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 Der entsprechende Anbieter muss auf dem Computer installiert sein, um eine Verbindung mit einer Datenquelle herzustellen.  
  
> [!NOTE]  
>  Beim Auswählen einer Datenbank auf dieser Seite werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Der Import ist jedoch nicht erfolgreich, wenn der auf der Seite Identitätswechselinformationen angegebene Benutzer nicht über ausreichend Berechtigungen zum Lesen aus der ausgewählten Datenbank verfügt.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Anzeigename der Verbindung**  
 Geben Sie einen eindeutigen Namen für diese Datenquellenverbindung ein. Dies ist ein Pflichtfeld.  
  
 **Server- oder Dateiname**  
 Geben Sie eine der folgenden Informationen an:  
  
-   Geben Sie den Namen oder die IP-Adresse des SQL Server Analysis Services-Servers ein, mit dem eine Verbindung hergestellt werden soll.  
  
     Sie können einen Punkt (.), (local) oder localhost zum Angeben des lokalen Servers verwenden.  
  
-   Geben Sie die URL einer PowerPivot-Arbeitsmappe ein, die in SharePoint veröffentlicht ist.  
  
 **Windows-Authentifizierung verwenden**  
 Geben Sie an, ob die Windows-Authentifizierung verwendet wird, um eine Verbindung mit einem SQL Server Analysis Services-Server herzustellen.  
  
 Der Windows-Authentifizierungsmodus ermöglicht Benutzern das Herstellen einer Verbindung über ein Windows-Benutzerkonto. Verwenden Sie nach Möglichkeit die Windows-Authentifizierung.  
  
 Wenn die Windows-Authentifizierung verwendet wird, werden die Anmeldeinformationen des aktuellen Benutzers beim Anzeigen von Daten in der Vorschau und beim Filtern von Daten im Fenster Tabelleneigenschaften und im Import-Assistenten verwendet. Diese Anmeldeinformationen werden nicht zum Importieren oder Aktualisieren von Daten verwendet, stattdessen werden die auf der Seite Identitätswechselinformationen angegebenen Windows-Anmeldeinformationen verwendet.  
  
 **SQL Server-Authentifizierung verwenden**  
 Geben Sie an, ob die SQL Server-Authentifizierung verwendet wird, um eine Verbindung mit einem SQL Server Analysis Services-Server herzustellen.  
  
 Mit der SQL Server-Authentifizierung führt SQL Server die Authentifizierung selbst aus, indem überprüft wird, ob ein SQL Server-Anmeldekonto eingerichtet wurde und ob das angegebene Kennwort mit dem zuvor aufgezeichneten übereinstimmt.  
  
 Die SQL Server-Authentifizierung wird zum Erstellen der Verbindungszeichenfolge für die Datenquelle verwendet. Diese Anmeldeinformationen werden auch beim Anzeigen von Daten in der Vorschau und beim Filtern von Daten im Fenster Tabelleneigenschaften und im Import-Assistenten verwendet. Diese Anmeldeinformationen werden nicht zum Importieren oder Aktualisieren von Daten verwendet, stattdessen werden die auf der Seite Identitätswechselinformationen angegebenen Windows-Anmeldeinformationen verwendet.  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen für die Datenbankverbindung an. Diese Option ist nur verfügbar, wenn Sie die Windows-Authentifizierung für die Verbindungsherstellung ausgewählt haben.  
  
 **Kennwort**  
 Geben Sie ein Kennwort für die Datenbankverbindung an. Sie können diese Option nur bearbeiten, wenn Sie zum Verbinden die SQL Server-Authentifizierung ausgewählt haben.  
  
 **Kennwort speichern**  
 Geben Sie an, ob das Kennwort, das Sie im Feld **Kennwort** eingegeben haben, gespeichert werden soll. Diese Option ist nur verfügbar, wenn Sie die SQL Server-Authentifizierung für die Verbindungsherstellung ausgewählt haben.  
  
 **Datenbankname**  
 Wählen Sie aus der Liste der Datenbanken eine Datenbank aus.  
  
 **Erweitert:**  
 Legen Sie zusätzliche Verbindungseigenschaften im Dialogfeld **Erweiterte Eigenschaften festlegen** fest. Weitere Informationen finden Sie unter [Festlegen von erweiterten Eigenschaften &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Verbindung testen**  
 Stellen Sie unter Verwendung der aktuellen Einstellungen eine Verbindung mit der Datenquelle her. Eine Meldung gibt Aufschluss darüber, ob die Verbindungsherstellung erfolgreich war.  
  
  
