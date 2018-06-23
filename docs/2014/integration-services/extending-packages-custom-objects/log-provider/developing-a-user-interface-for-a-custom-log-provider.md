---
title: Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten Protokollanbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c60ec7f24dd5d6970697f112329e2d82b2e22af5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150635"
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a>Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten Protokollanbieter
  Viele [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Protokollanbieter verfügen über eine benutzerdefinierte Benutzeroberfläche, die <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> implementiert und das Textfeld **Konfiguration** im Dialogfeld **SSIS-Protokolle konfigurieren** durch eine gefilterte Dropdownliste der verfügbaren Verbindungs-Manager ersetzt. Individuelle Benutzeroberflächen für benutzerdefinierte Protokollanbieter werden in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] jedoch nicht implementiert.  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben Sie mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines benutzerdefinierten Protokollanbieters](creating-a-custom-log-provider.md)   
 [Codieren eines benutzerdefinierten Protokollanbieters](coding-a-custom-log-provider.md)  
  
  