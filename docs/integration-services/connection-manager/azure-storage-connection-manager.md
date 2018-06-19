---
title: Azure Storage-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 25338d4e05ab8c6cb7a4008230a340dc339e9bbd
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35409952"
---
# <a name="azure-storage-connection-manager"></a>Azure Storage-Verbindungs-Manager
  Der **Azure Storage-Verbindungs-Manager** ermöglicht es, eine Verbindung zwischen einem SSIS-Paket und einem Azure Storage-Konto mithilfe der Werte zu erstellen, die Sie für die Eigenschaften „Speicherkontoname“ und „Kontoschlüssel“ angeben.  
   
 Der **Azure Storage-Verbindungs-Manager** ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
1.  Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **AzureStorage**aus, und klicken Sie auf **Hinzufügen**.  
  
2.  Wählen Sie im Editor-Dialogfeld „Azure Storage-Verbindungs-Manager“ **Azure-Konto verwenden** aus, um eine Verbindung zu einem Azure Storage-Dienst über das Internet herzustellen, oder wählen Sie **Lokales Entwicklerkonto verwenden** aus, um eine Verbindung zum lokalen Dienst herzustellen, der vom Azure Storage-Emulator gehostet wird.  
  
3.  Gehen Sie bei Auswahl von **Azure-Konto verwenden** folgendermaßen vor:  
  
    1.  Geben Sie Werte in die Felder **Speicherkontoname** und **Kontoschlüssel** an. Diese Werte werden als vertrauliche Daten im SSIS-Paket gespeichert.  
  
    2.  Wählen Sie **HTTPS verwenden** aus, wenn Sie HTTPS anstelle von HTTP für die Verbindung mit dem Azure Storage-Dienst verwenden möchten.  
  
4.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
5.  Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.  
  
  
