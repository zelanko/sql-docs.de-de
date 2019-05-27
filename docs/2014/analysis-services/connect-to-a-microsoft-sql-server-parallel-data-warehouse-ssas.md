---
title: Herstellen einer Verbindung von einem Microsoft SQL Server Parallel Datawarehouse (SSAS) mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlparadatawh.f1
ms.assetid: 98c879ee-7257-40c9-bc85-6766bd3b4885
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7ab10518ff976562665317a75574ee2070be0d8f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66087199"
---
# <a name="connect-to-a-microsoft-sql-server-parallel-data-warehouse-ssas"></a>Verbindung mit Microsoft SQL Server Parallel Data Warehouse herstellen (SSAS)
  Auf dieser Seite des **Tabellenimport-Assistenten** können Sie Einstellungen angeben, um eine Verbindung mit Microsoft SQL Server Parallel Data Warehouse (PDW) herzustellen. Um im [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf den Assistenten zuzugreifen, klicken Sie im Menü **Modell** auf **Aus Datenquelle importieren**.  
  
 SQL Server PDW ist eine hochskalierbare Anwendung, die Leistung zu niedrigen Preisen durch massive Parallelverarbeitung bietet. Weitere Informationen zu SQL Server PDW finden Sie auf der Website [SQL Server 2008 R2 Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895). Sie stellen mithilfe der SQL Server-Authentifizierung eine Verbindung mit dem Data Warehouse her. Der entsprechende Anbieter muss auf dem Computer installiert sein, um eine Verbindung mit einer Datenquelle herzustellen.  
  
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
  
 **Erweitert**  
 Legen Sie zusätzliche Verbindungseigenschaften im Dialogfeld **Erweiterte Eigenschaften festlegen** fest. Weitere Informationen finden Sie unter [Festlegen von erweiterten Eigenschaften &#40;SSAS&#41;](set-advanced-properties-ssas.md).  
  
 **Verbindung testen**  
 Stellen Sie unter Verwendung der aktuellen Einstellungen eine Verbindung mit der Datenquelle her. Eine Meldung gibt Aufschluss darüber, ob die Verbindungsherstellung erfolgreich war.  
  
  
