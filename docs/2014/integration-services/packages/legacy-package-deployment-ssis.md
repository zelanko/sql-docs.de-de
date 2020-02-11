---
title: Paket Bereitstellung (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, deploying
- deploying packages [Integration Services]
- SQL Server Integration Services packages, deploying
- deploying packages [Integration Services], about deploying packages
- packages [Integration Services], deploying
- SSIS packages, deploying
ms.assetid: 0f5fc7be-e37e-4ecd-ba99-697c8ae3436f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c912d4417842bc332262549cc604b97eaa50a44d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62767089"
---
# <a name="package-deployment-ssis"></a>Paketbereitstellung (SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthält Tools und Assistenten, mit denen Pakete vom Entwicklungs Computer auf dem Produktionsserver oder anderen Computern problemlos bereitgestellt werden können.  
  
 Das Paketbereitstellungsverfahren gliedert sich in vier Schritte:  
  
1.  Der erste Schritt ist optional und umfasst das Erstellen von Paketkonfigurationen, die Eigenschaften von Paketelementen zur Laufzeit aktualisieren. Diese Konfigurationen werden beim Bereitstellen der Pakete automatisch mit eingeschlossen.  
  
2.  Im zweiten Schritt wird das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt erstellt, um damit ein Paketbereitstellungshilfsprogramm zu erstellen. Das Bereitstellungshilfsprogramm für das Projekt enthält die Pakete, die Sie bereitstellen möchten.  
  
3.  Im dritten Schritt wird der Bereitstellungsordner, den Sie beim Erstellen des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekts erstellt haben, auf den Zielcomputer kopiert.  
  
4.  Im vierten Schritt wird auf dem Zielcomputer der Paketinstallations-Assistent ausgeführt, um damit die Pakete auf dem Dateisystem oder einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu installieren.  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Erstellen eines Bereitstellungshilfsprogramms finden Sie unter [Erstellen eines Bereitstellungs-Hilfsprogramms](../create-a-deployment-utility.md).  
  
 Informationen zum Bereitstellen von Paketen mit dem Bereitstellungshilfsprogramm finden Sie unter [Bereitstellen von Paketen mithilfe des Bereitstellungshilfsprogramms](../deploy-packages-by-using-the-deployment-utility.md).  
  
 Informationen zum Erstellen von Paketkonfigurationen finden Sie unter [Erstellen von Paketkonfigurationen](../create-package-configurations.md).  
  
  
