---
title: Herstellen einer Verbindung mit einer Microsoft SQL Server Datenbank (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserverdb.f1
ms.assetid: 6ebfe029-dbba-4f0d-a556-328e79ef629f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0c291dbc9903fddfa714f9b1665d7ba9d4265a0f
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527176"
---
# <a name="connect-to-a-microsoft-sql-server-database-ssas"></a>Mit einer Microsoft SQL Server-Datenbank verbinden (SSAS)
  Auf dieser Seite des **Tabellenimport-Assistenten** können Sie Einstellungen angeben, um eine Verbindung mit einer Microsoft SQL Server-Datenbank herzustellen. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 Der entsprechende Anbieter muss auf dem Computer installiert sein, um eine Verbindung mit einer Datenquelle herzustellen.  
  
> [!NOTE]  
>  Beim Auswählen einer Datenbank auf dieser Seite werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Der Import ist jedoch nicht erfolgreich, wenn der auf der Seite Identitätswechselinformationen angegebene Benutzer nicht über ausreichend Berechtigungen zum Lesen aus der ausgewählten Datenbank verfügt.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
 **Anzeigename der Verbindung**  
 Geben Sie einen eindeutigen Namen für diese Datenquellenverbindung ein. Dies ist ein Pflichtfeld.  
  
 **Servername**  
 Wählen Sie den Namen der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz aus, mit der eine Verbindung hergestellt werden soll, oder geben Sie den Namen oder die IP-Adresse ein.  
  
 Sie können einen Punkt (.), (local) oder localhost zum Angeben des lokalen Servers verwenden.  
  
 **Windows-Authentifizierung verwenden**  
 Geben Sie an, ob die Windows-Authentifizierung verwendet werden soll, um eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]herzustellen.  
  
 Der Windows-Authentifizierungsmodus ermöglicht Benutzern das Herstellen einer Verbindung über ein Windows-Benutzerkonto. Verwenden Sie nach Möglichkeit die Windows-Authentifizierung.  
  
 Wenn die Windows-Authentifizierung verwendet wird, werden die Anmeldeinformationen des aktuellen Benutzers beim Anzeigen von Daten in der Vorschau und beim Filtern von Daten im Fenster Tabelleneigenschaften und im Import-Assistenten verwendet. Diese Anmeldeinformationen werden nicht zum Importieren oder Aktualisieren von Daten verwendet, stattdessen werden die auf der Seite Identitätswechselinformationen angegebenen Windows-Anmeldeinformationen verwendet.  
  
 **SQL Server Authentifizierung verwenden**  
 Geben Sie an, ob die SQL Server-Authentifizierung verwendet werden soll, um eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]herzustellen.  
  
 Mit der SQL Server-Authentifizierung führt SQL Server die Authentifizierung selbst aus, indem überprüft wird, ob ein SQL Server-Anmeldekonto eingerichtet wurde und ob das angegebene Kennwort mit dem zuvor aufgezeichneten übereinstimmt.  
  
 Die SQL Server-Authentifizierung wird zum Erstellen der Verbindungszeichenfolge für die Datenquelle verwendet. Diese Anmeldeinformationen werden auch beim Anzeigen von Daten in der Vorschau und beim Filtern von Daten im Fenster Tabelleneigenschaften und im Import-Assistenten verwendet. Diese Anmeldeinformationen werden nicht zum Importieren oder Aktualisieren von Daten verwendet, stattdessen werden die auf der Seite Identitätswechselinformationen angegebenen Windows-Anmeldeinformationen verwendet.  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen für die Datenbankverbindung an. Diese Option ist nur verfügbar, wenn Sie die SQL Server-Authentifizierung für die Verbindungsherstellung ausgewählt haben.  
  
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
  
  
