---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bddf6ce0bbfb78435118ef3d87303a94c792c96d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922646"
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


