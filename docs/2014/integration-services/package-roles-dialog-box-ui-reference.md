---
title: Referenz zur Benutzeroberfläche des Dialogfelds Rollen-Paket | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- Package Roles dialog box
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d45ea589ee41aa5895acf0ee1c475aea19bbaeed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225210"
---
# <a name="package-roles-dialog-box-ui-reference"></a>Referenz zur Benutzeroberfläche des Dialogfelds Paketrollen
  Verwenden Sie das Dialogfeld **Paketrollen**, das in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] verfügbar ist, um die Rollen auf Datenbankebene anzugeben, die Lesezugriff auf das Paket besitzen, sowie die Rollen auf Datenbankebene, die Schreibzugriff auf das Paket besitzen. Rollen auf Datenbankebene gelten nur für Pakete, die in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb**-Datenbank gespeichert sind.  
  
 Weitere Informationen zu den Rollen auf Datenbankebene von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] und ihren Berechtigungen finden Sie unter [Integration Services-Rollen &#40;SSIS-Dienst&#41;](security/integration-services-roles-ssis-service.md).  
  
 Die im Dialogfeld aufgeführten Rollen sind die aktuellen Rollen der **msdb** -Systemdatenbank. Wenn keine Rollen ausgewählt sind, gelten die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Standardrollen. Standardmäßig enthält die Leserolle **db_ssisadmin**, **db_ssisoperator**und den Benutzer, der das Paket erstellt hat. Ein Benutzer, der Mitglied einer dieser Rollen ist oder die Pakete erstellt hat, kann Pakete aufzählen, anzeigen, exportieren und ausführen. Standardmäßig schließt die Schreibrolle **db_ssisadmin** und den Benutzer ein, der das Paket erstellt hat. Ein Benutzer, der Mitglied dieser Rolle ist, und der Benutzer, der die Pakete erstellt hat, kann Pakete importieren, löschen und ändern.  
  
 Die **ownersid** -Spalte in der **sysssispackages** -Tabelle enthält die eindeutige Sicherheits-ID des Benutzers, der das Paket erstellt hat.  
  
## <a name="options"></a>Tastatur  
 **Paketname**  
 Gibt den Namen des Pakets an.  
  
 **Leserolle**  
 Auswählen einer Rolle in der Liste.  
  
 **Schreibrolle**  
 Auswählen einer Rolle in der Liste  
  
## <a name="see-also"></a>Siehe auch  
 [Rollen auf Datenbankebene](../relational-databases/security/authentication-access/database-level-roles.md)   
 [Übersicht über die Sicherheit &#40;Integrationsdienste&#41;](security/security-overview-integration-services.md)  
  
  
