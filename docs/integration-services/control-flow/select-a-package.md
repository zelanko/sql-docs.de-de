---
title: Paket auswählen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8cc976451c29c6d0b1656fec456b2a46b1f4f5f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65727481"
---
# <a name="select-a-package"></a>Paket auswählen

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Mithilfe des Dialogfelds **Paket auswählen** können Sie das Paket angeben, von dem der Task Nachrichtenwarteschlange Nachrichten empfangen kann.  
  
## <a name="static-options"></a>Statische Optionen  
 **Speicherort**  
 Geben Sie den Speicherort des Pakets an. Diese Eigenschaft besitzt die in der folgenden Tabelle aufgeführten Optionen.  
  
|value|und Beschreibung|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Legt den Speicherort als Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fest. Wenn Sie diesen Wert auswählen, werden die dynamischen Optionen **Server**, **Windows-Authentifizierung verwenden**, **SQL Server-Authentifizierung verwenden**, **Benutzername**und **Kennwort**angezeigt.|  
|DTSX-Datei|Legt als Speicherort eine DTSX-Datei fest. Wenn Sie diesen Wert auswählen, wird die dynamische Option **Dateiname**angezeigt.|  
  
## <a name="location-dynamic-options"></a>Dynamische Optionen für Location  
  
### <a name="location--sql-server"></a>Location = SQL Server  
 **Paketname**  
 Wählen Sie ein Paket aus, das auf dem angegebenen Server gespeichert ist.  
  
 **Server**  
 Geben Sie einen Servernamen an, oder wählen Sie einen Server aus der Liste aus.  
  
 **Windows-Authentifizierung verwenden**  
 Klicken Sie auf diese Option, wenn die Windows-Authentifizierung verwendet werden soll.  
  
 **SQL Server-Authentifizierung verwenden**  
 Klicken Sie auf diese Option, wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet werden soll.  
  
 **User name**  
 Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden, geben Sie einen Benutzernamen an, der zur Anmeldung beim Server verwendet wird.  
  
 **Kennwort**  
 Geben Sie ein Kennwort an, falls Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwenden.  
  
### <a name="location--dtsx-file"></a>Speicherort = DTSX-Datei  
 **Dateiname**  
 Geben Sie den Pfad eines Pakets an, oder klicken Sie auf die Schaltfläche zum Durchsuchen **(…)** , um das Paket zu suchen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Nachrichtenwarteschlange (Task)](../../integration-services/control-flow/message-queue-task.md)  
  
  
