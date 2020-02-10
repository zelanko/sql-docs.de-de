---
title: Protokollierung für Pakete mit Lastenausgleich auf Remote Servern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], remote packages
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 64dec3a89b883d6b3234f65896bb89d3bfde5305
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057855"
---
# <a name="logging-for-load-balanced-packages-on-remote-servers"></a>Protokollierung für Pakete auf Remoteservern, für die ein Lastenausgleich ausgeführt wurde
  Für einen Administrator ist es einfacher, die Protokolle aller untergeordneten Pakete, die auf verschiedenen Servern ausgeführt werden, zu verwalten, wenn alle untergeordneten Pakete denselben Protokollanbieter verwenden und in dasselbe Ziel schreiben. Eine Möglichkeit zum Erstellen einer allgemeinen Protokolldatei für alle untergeordneten Pakete besteht darin, die untergeordneten Pakete für die Protokollierung ihrer Ereignisse in einem SQL Server-Protokollanbieter zu konfigurieren. Sie können alle Pakete für die Verwendung derselben Datenbank, desselben Servers und derselben Server-Instanz konfigurieren.  
  
 Zum Anzeigen der Protokolldateien muss sich der Administrator lediglich bei einem einzigen Server anmelden, um die Protokolldateien aller untergeordneten Pakete anzuzeigen.  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen über das Ermöglichen des Anmeldens in einem Paket finden Sie unter [Aktivieren der Paketprotokollierung in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Protokollierung &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
