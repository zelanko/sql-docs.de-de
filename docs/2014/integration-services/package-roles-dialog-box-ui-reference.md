---
title: Referenz zur Benutzeroberfläche des Dialog Felds Paket Rollen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.packageroles.f1
helpviewer_keywords:
- Package Roles dialog box
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 64cdb71f323a4ac9325da74503d8aebaa8dd4474
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964850"
---
# <a name="package-roles-dialog-box-ui-reference"></a>Referenz zur Benutzeroberfläche des Dialogfelds Paketrollen
  Verwenden Sie das Dialogfeld **Paketrollen** , das in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]verfügbar ist, um die Rollen auf Datenbankebene anzugeben, die Lesezugriff auf das Paket besitzen, sowie die Rollen auf Datenbankebene, die Schreibzugriff auf das Paket besitzen. Rollen auf Datenbankebene gelten nur für Pakete, die in der -Datenbank [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **msdb** gespeichert sind.  
  
 Weitere Informationen zu den Rollen auf Datenbankebene von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] und ihren Berechtigungen finden Sie unter [Integration Services-Rollen &#40;SSIS-Dienst&#41;](security/integration-services-roles-ssis-service.md).  
  
 Die im Dialogfeld aufgeführten Rollen sind die aktuellen Rollen der **msdb** -Systemdatenbank. Wenn keine Rollen ausgewählt sind, gelten die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Standardrollen. Standardmäßig enthält die Leserolle **db_ssisadmin**, **db_ssisoperator**und den Benutzer, der das Paket erstellt hat. Ein Benutzer, der Mitglied einer dieser Rollen ist oder die Pakete erstellt hat, kann Pakete aufzählen, anzeigen, exportieren und ausführen. Standardmäßig schließt die Schreibrolle **db_ssisadmin** und den Benutzer ein, der das Paket erstellt hat. Ein Benutzer, der Mitglied dieser Rolle ist, und der Benutzer, der die Pakete erstellt hat, kann Pakete importieren, löschen und ändern.  
  
 Die **ownersid** -Spalte in der **sysssispackages** -Tabelle enthält die eindeutige Sicherheits-ID des Benutzers, der das Paket erstellt hat.  
  
## <a name="options"></a>Tastatur  
 **Paketname**  
 Gibt den Namen des Pakets an.  
  
 **Leser-Rolle**  
 Auswählen einer Rolle in der Liste.  
  
 **Schreibrolle**  
 Auswählen einer Rolle in der Liste  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rollen auf Datenbankebene](../relational-databases/security/authentication-access/database-level-roles.md)   
 [Sicherheitsübersicht &#40;Integration Services&#41;](security/security-overview-integration-services.md)  
  
  
