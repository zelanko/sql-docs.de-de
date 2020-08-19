---
description: Command-Objekt – Übersicht
title: Übersicht über das Befehls Objekt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
author: rothja
ms.author: jroth
ms.openlocfilehash: d44c727a69dc74bf243bc2f2c0204cb41cd9f585
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453682"
---
# <a name="command-object-overview"></a>Command-Objekt – Übersicht
Mit einem **Command** -Objekt können Sie folgende Aufgaben ausführen:  
  
-   Definieren Sie den ausführbaren Text des Befehls (z. b. eine SQL-Anweisung oder eine gespeicherte Prozedur), indem Sie die **CommandText** -Eigenschaft verwenden.  
  
-   Definieren Sie parametrisierte Abfragen oder Argumente für gespeicherte Prozeduren mithilfe von **Parameter** Objekten und der **Parameter** Auflistung.  
  
-   Führen Sie einen Befehl aus, und geben Sie, falls zutreffend, mithilfe der **Execute** -Methode ein **Recordset** -Objekt zurück.  
  
-   Geben Sie den Befehlstyp mithilfe der **CommandType** -Eigenschaft vor der Ausführung an, um die Leistung zu optimieren.  
  
-   Geben Sie mithilfe der Eigenschaft **Dialekt** des **Befehls** Objekts bestimmte Informationen über den Befehls Text an.  
  
-   Steuert, ob der Anbieter vor der Ausführung mithilfe der **vorbereiteten** Eigenschaft eine vorbereitete (oder kompilierte) Version des Befehls speichert.  
  
-   Legen Sie die Anzahl von Sekunden fest, die ein Anbieter auf die Ausführung eines Befehls wartet, indem die **CommandTimeout** -Eigenschaft verwendet wird.  
  
-   Ordnen Sie eine geöffnete Verbindung einem **Befehls** Objekt zu, indem Sie die zugehörige **ActiveConnection** -Eigenschaft festlegen.  
  
-   Legen Sie die **Name** -Eigenschaft fest, um das **Command** -Objekt als Methode für das zugeordnete **Verbindungs** Objekt zu identifizieren.  
  
-   Übergeben Sie ein **Command** -Objekt an die **Quell** Eigenschaft eines **Recordsets** , um Daten abzurufen.  
  
-   Übergeben Sie ein **Streamobjekt** mit einem Befehl (z. b. einem XML-Befehl) an einen Anbieter, der ihn unterstützt.
