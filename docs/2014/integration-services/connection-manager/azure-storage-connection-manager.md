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
ms.openlocfilehash: c6b6c86aa3f76088ff3cb0e36a1a111b325944ea
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84921091"
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
  
  
