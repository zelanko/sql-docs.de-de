---
title: Eigenschaften von SQL Server-Browser (Registerkarte „Anmelden“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 8cad70eb2853af996a87295cb2f39daea1a2daa0
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733238"
---
# <a name="sql-server-browser-properties-log-on-tab"></a>Eigenschaften von SQL Server-Browser (Registerkarte Anmelden)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Programm wird als Dienst auf dem Server ausgeführt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser lauscht auf eingehende Anforderungen für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressourcen und stellt Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen zur Verfügung, die auf dem Computer installiert sind.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser lauscht an einem UDP-Port. Nicht authentifizierte Anforderungen werden mithilfe von SSRP ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol) akzeptiert.  
  
 Das Ändern eines Kennworts für ein Konto wird sofort wirksam. Es ist kein Neustart des Dienstes erforderlich.  
  
## <a name="options"></a>enthalten  
 **Lokales System**  
 Führen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst im Sicherheitskontext des lokalen Systemkontos aus. Verwenden Sie nach Möglichkeit ein Konto mit geringen Berechtigungen.  
  
 **Dieses Konto**  
 Geben Sie ein lokales oder ein Domänenbenutzerkonto an, das die Windows-Authentifizierung verwendet. Das Verwenden eines Domänenbenutzerkontos mit minimalen Berechtigungen für Dienste wird empfohlen. Informationen zum Auswählen eines Kontos finden Sie unter "Einrichten von Windows-Dienstkonten" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
 **Durchsuchen**  
 Suchen Sie nach einem Benutzer oder einem integriertem Sicherheitsprinzipal.  
  
> [!IMPORTANT]  
>  Verwenden Sie ein Konto mit geringen Berechtigungen. Informationen zu den Berechtigungen, die für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst erforderlich sind, finden Sie im Abschnitt „Sicherheit“ von [SQL Server-Browserdienst](../../tools/configuration-manager/sql-server-browser-service.md).  
  
 **Kennwort**  
 Geben Sie das Kennwort des Sicherheitsprinzipals ein.  
  
 **Kennwort bestätigen**  
 Bestätigen Sie das Kennwort des Sicherheitsprinzipals.  
  
 **Dienststatus**  
 Zeigt an, ob dieser Dienst ausgeführt wird, angehalten oder deaktiviert ist. „ **…** “ gibt einen ausstehenden Statuswechsel an.  
  
 **Start**  
 Starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst.  
  
 **Beenden**  
 Beenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst.  
  
 **Anhalten**  
 Halten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst an.  
  
 **Fortsetzen**  
 Setzen Sie die Ausführung eines angehaltenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdiensts fort.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Browserdienst](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
