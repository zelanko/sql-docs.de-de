---
title: Herstellen einer Verbindung mit Microsoft SQL Server Analysis Services (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserveras.f1
ms.assetid: 7f3244ee-b690-471c-893d-68e361c2d416
author: minewiskan
ms.author: owend
ms.openlocfilehash: 558f9936b7a8e78b3ef75f3bb525185ae497959c
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84526966"
---
# <a name="connect-to-microsoft-sql-server-analysis-services-ssas"></a>Verbindung mit Microsoft SQL Server Analysis Services herstellen (SSAS)
  Auf dieser Seite des **Tabellen Import-Assistenten** können Sie Einstellungen für das Importieren von Daten aus einem Microsoft SQL Server Analysis Services Cube oder einer auf SharePoint gehosteten Power Pivot-Arbeitsmappe angeben. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 Der entsprechende Anbieter muss auf dem Computer installiert sein, um eine Verbindung mit einer Datenquelle herzustellen.  
  
> [!NOTE]  
>  Beim Auswählen einer Datenbank auf dieser Seite werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Der Import ist jedoch nicht erfolgreich, wenn der auf der Seite Identitätswechselinformationen angegebene Benutzer nicht über ausreichend Berechtigungen zum Lesen aus der ausgewählten Datenbank verfügt.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
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
  
 **SQL Server Authentifizierung verwenden**  
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
  
 **Erweitert**  
 Legen Sie zusätzliche Verbindungseigenschaften im Dialogfeld **Erweiterte Eigenschaften festlegen** fest. Weitere Informationen finden Sie unter [Festlegen von erweiterten Eigenschaften &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Testen der Verbindung**  
 Stellen Sie unter Verwendung der aktuellen Einstellungen eine Verbindung mit der Datenquelle her. Eine Meldung gibt Aufschluss darüber, ob die Verbindungsherstellung erfolgreich war.  
  
  
