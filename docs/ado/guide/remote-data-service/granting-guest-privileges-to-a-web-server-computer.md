---
description: Gewähren von Gastberechtigungen für einen Webservercomputer
title: Gewähren von Gast Berechtigungen für einen Webserver Computer | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
author: rothja
ms.author: jroth
ms.openlocfilehash: 9fa62e95920e8a4aece0f7b6833c635cfdbf7b09
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452182"
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Gewähren von Gastberechtigungen für einen Webservercomputer
Das anonyme Webserver Konto (IUSR_*Computername*) muss der lokalen Gruppe "Gäste" auf dem Webserver Computer hinzugefügt werden, um RDS zu verwenden.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>So erteilen Sie einem Webserver Computer Gast Berechtigungen  
  
1.  Klicken Sie auf Ihrem Microsoft Windows 2000-Server Computer auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Verwaltung**, und klicken Sie dann auf **Computer Verwaltung**.  
  
2.  Klicken Sie in der Konsolen Struktur unter **lokale Benutzer und Gruppen**auf **Gruppen**.  
  
3.  Wählen Sie die lokale Gruppe **Gäste** aus. Wählen Sie im Menü **Aktion** die Option **Eigenschaften**aus.  
  
4.  Klicken Sie im Dialogfeld **Gast Eigenschaften** auf **Hinzufügen**.  
  
5.  Wenn das anonyme Webserver Konto nicht in der Liste im Dialogfeld **Benutzer oder Gruppen auswählen** angezeigt wird, geben Sie den Namen (IUSR_*Computername*) in das Feld unten leer ein, und klicken Sie dann auf **Hinzufügen**.  
  
6.  Klicken Sie auf **OK**.


