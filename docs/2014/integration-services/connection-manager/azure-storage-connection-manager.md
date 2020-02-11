---
title: Azure Storage-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpstorageconn.f1
- sql11.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ea689f96911af35176d6467e73d496b59f35e3c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62833558"
---
# <a name="azure-storage-connection-manager"></a>Azure Storage-Verbindungs-Manager
  Der Azure Storage-Verbindungs-Manager ermöglicht das Verbinden eines SSIS-Pakets mit einem Azure Storage-Konto mit den Werten, die Sie für die Eigenschaften angeben: Speicherkontoname und Kontoschlüssel.  
  
1.  Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **AzureStorage**aus, und klicken Sie auf **Hinzufügen**.  
  
2.  Wählen Sie im Editor-Dialogfeld „Azure Storage-Verbindungs-Manager“ **Azure-Konto verwenden** aus, um eine Verbindung zu einem Azure Storage-Dienst über das Internet herzustellen, oder wählen Sie **Lokales Entwicklerkonto verwenden** aus, um eine Verbindung zum lokalen Dienst herzustellen, der vom Azure Storage-Emulator gehostet wird.  
  
3.  Gehen Sie bei Auswahl von **Azure-Konto verwenden** folgendermaßen vor:  
  
    1.  Geben Sie Werte in die Felder **Speicherkontoname** und **Kontoschlüssel** an. Diese Werte werden als vertrauliche Daten im SSIS-Paket gespeichert.  
  
    2.  Wählen Sie **HTTPS verwenden** aus, wenn Sie HTTPS anstelle von HTTP für die Verbindung mit dem Azure Storage-Dienst verwenden möchten.  
  
4.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
5.  Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.  
  
  
