---
title: Herstellen einer Verbindung einer Azure SQL-Datenbank (SSAS) mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlazure.f1
ms.assetid: 4e0344e9-1822-4698-ad22-05f1f341ced7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 94a830bba0339262148a0a7f826f3bcb89371274
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62680241"
---
# <a name="connect-to-an-azure-sql-database-ssas"></a>Mit einer Azure SQL-Datenbank verbinden (SSAS)
  Auf dieser Seite des **Tabellenimport-Assistenten** können Sie eine Verbindung mit einer [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] herstellen. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
> [!NOTE]  
>  Wenn Sie eine Verbindung mit einem Azure DataMarket-Dataset herstellen, gehen Sie zu [Mit einem Bericht oder Datenfeed verbinden &#40;SSAS&#41;](connect-to-a-report-or-data-feed-ssas.md).  
  
 Die [!INCLUDE[ssSDS](../includes/sssds-md.md)] ist eine gehostete, relationale Datenbank, mit der Sie eine Verbindung unter Verwendung der SQL Server-Authentifizierung herstellen. Weitere Informationen zu [!INCLUDE[ssSDS](../includes/sssds-md.md)]finden Sie auf der Website zu [SQL-Datenbanken](https://go.microsoft.com/fwlink/?LinkID=157856). Der entsprechende Anbieter muss auf dem Computer installiert sein, um eine Verbindung mit einer Datenquelle herzustellen.  
  
> [!NOTE]  
>  Beim Auswählen einer Datenbank auf dieser Seite werden die Anmeldeinformationen des aktuellen Benutzers verwendet. Der Import ist jedoch nicht erfolgreich, wenn der auf der Seite Identitätswechselinformationen angegebene Benutzer nicht über ausreichend Berechtigungen zum Lesen aus der ausgewählten Datenbank verfügt.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Anzeigename der Verbindung**  
 Geben Sie einen eindeutigen Namen für diese Datenquellenverbindung ein. Dies ist ein Pflichtfeld.  
  
 **Servername**  
 Geben Sie den Namen oder die IP-Adresse des Servers ein, zu dem eine Verbindung hergestellt werden soll.  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen für die Datenbankverbindung an.  
  
 Dieser Benutzername wird beim Erstellen der Verbindungszeichenfolge für die Datenquelle verwendet. Diese Anmeldeinformationen werden auch beim Anzeigen von Daten in der Vorschau und beim Filtern von Daten im Fenster Tabelleneigenschaften und im Import-Assistenten verwendet. Diese Anmeldeinformationen werden nicht zum Importieren oder Aktualisieren von Daten verwendet, stattdessen werden die auf der Seite Identitätswechselinformationen angegebenen Windows-Anmeldeinformationen verwendet.  
  
 **Kennwort**  
 Geben Sie ein Kennwort für die Datenbankverbindung an.  
  
 **Kennwort speichern**  
 Geben Sie an, ob das Kennwort, das Sie im Feld **Kennwort** eingegeben haben, gespeichert werden soll.  
  
 **Datenbankname**  
 Wählen Sie aus der Liste der Datenbanken eine Datenbank aus.  
  
 **Erweitert:**  
 Legen Sie zusätzliche Verbindungseigenschaften im Dialogfeld **Erweiterte Eigenschaften festlegen** fest. Weitere Informationen finden Sie unter [Festlegen von erweiterten Eigenschaften &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Verbindung testen**  
 Stellen Sie unter Verwendung der aktuellen Einstellungen eine Verbindung mit der Datenquelle her. Eine Meldung gibt Aufschluss darüber, ob die Verbindungsherstellung erfolgreich war.  
  
  
