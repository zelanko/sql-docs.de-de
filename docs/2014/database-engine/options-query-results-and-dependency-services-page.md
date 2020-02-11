---
title: Optionen (Seite "Abfrageergebnisse und Abhängigkeits Dienste") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: b9200880a9581b3903985c16fc2af129d19aceec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65481203"
---
# <a name="options-query-results-and-dependency-services-page"></a>Optionen (Abfrageergebnisse und Seite „Abhängigkeitsdienste“)
  Geben Sie auf dieser Seite den Server an, mit dem eine Verbindung für Abhängigkeitsdienste hergestellt werden soll. Mithilfe von Abhängigkeitsdiensten können Sie Informationen zu Abhängigkeiten zwischen [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Objekten und [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Objekten extrahieren, die auf anderen Servern gespeichert sind. Objektabhängigkeiten werden mithilfe des Dialog Felds **Objektabhängigkeiten** in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]angezeigt.  
  
 **Was möchten Sie tun?**  
  
1.  [Öffnen des Dialogfelds "Optionen" (Seite "Abfrageergebnisse"/"Abhängigkeitsdienste")](#open_dialog)  
  
2.  [Konfigurieren der Optionen](#options)  
  
##  <a name="open_dialog"></a>Öffnen Sie das Dialog Feld Optionen (Seite Abfrageergebnisse/Abhängigkeits Dienste).  
  
1.  Klicken [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]Sie in **im Menü Extras** auf **Optionen** .  
  
2.  Erweitern Sie **Abfrageergebnisse**, und klicken Sie dann auf **Abhängigkeitsdienste**.  
  
##  <a name="options"></a> Konfigurieren der Optionen  
  
### <a name="options"></a>Tastatur  
 **Dependency Services-Server**  
 Geben Sie den Server an, auf dem die Abhängigkeitsdienste installiert sind.  
  
 **Authentifizierung**  
 Wählen Sie die Windows-Authentifizierung aus, um sich mithilfe eines Microsoft Windows-Benutzerkontos anzumelden, oder wählen Sie die SQL Server-Authentifizierung aus.  
  
 Wenn ein Benutzer eine Verbindung mit einem angegebenen Benutzernamen und einem Kennwort von einer nicht vertrauenswürdigen Verbindung herstellt, führt SQL Server die Authentifizierung aus, indem überprüft wird, ob ein SQL Server-Anmeldekonto eingerichtet wurde und ob das angegebene Kennwort mit dem zuvor aufgezeichneten übereinstimmt. Wenn SQL Server das Anmeldekonto nicht finden kann, schlägt die Authentifizierung fehl und der Benutzer erhält eine Fehlermeldung.  
  
 **Benutzername**  
 Wenn Sie die SQL Server-Authentifizierung verwenden, geben Sie einen Benutzernamen an.  
  
 **Kennwort**  
 Geben Sie ein Kennwort an, wenn Sie die SQL Server-Authentifizierung verwenden.  
  
 **Test**  
 Klicken Sie auf die Option, um die Verbindung zu überprüfen.