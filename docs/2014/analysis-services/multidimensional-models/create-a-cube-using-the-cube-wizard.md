---
title: Erstellen eines Cubes mithilfe des Cube-Assistenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], creating
ms.assetid: d46d659c-3a4e-4364-94ac-f5eb6ba0ec25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7545bc1e1ad37ff395f3e4c3f65b1cb4614e533e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087032"
---
# <a name="create-a-cube-using-the-cube-wizard"></a>Erstellen eines Cubes mit dem Cube-Assistenten
  Sie können einen neuen Cube erstellen, indem Sie den Cube-Assistenten von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]verwenden.  
  
### <a name="to-create-a-new-cube"></a>So erstellen Sie einen neuen Cube  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Cubes**, und klicken Sie dann auf **Neuer Cube**.  
  
2.  Wählen Sie auf der Seite **Erstellungsmethode auswählen** des Cube-Assistenten die Option **Vorhandene Tabellen verwenden**aus, und klicken Sie dann auf **Weiter**.  
  
    > [!NOTE]  
    >  Möglicherweise müssen Sie gelegentlich einen Cube ohne vorhandene Tabellen erstellen. Um einen leeren Cube zu erstellen, wählen Sie **Leeren Cube erstellen**aus. Um Tabellen zu generieren, wählen Sie **Tabellen in der Datenquelle generieren**aus.  
  
3.  Führen Sie auf der Seite **Measuregruppentabellen auswählen** folgende Schritte aus:  
  
    1.  Wählen Sie in der Liste **Datenquellensicht** eine Datenquellensicht aus.  
  
    2.  Wählen Sie in der Liste **Measuregruppentabellen** die Tabellen aus, die verwendet werden, um Measuregruppen zu erstellen.  
  
    3.  Klicken Sie auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Measures auswählen** die Measures aus, die Sie in den Cube einschließen möchten, und klicken Sie dann auf **Weiter**.  
  
     Optional können Sie die Namen der Measures und der Measuregruppen ändern.  
  
5.  Wählen Sie auf der Seite **Vorhandene Dimensionen auswählen** die vorhandenen Dimensionen aus, die in den Cube eingeschlossen werden sollen, und klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Die Seite **Vorhandene Dimensionen auswählen** wird angezeigt, wenn für eine der ausgewählten Measuregruppe bereits Dimensionen in der Datenbank vorhanden sind.  
  
6.  Wählen Sie auf der Seite **Neue Dimensionen auswählen** die neuen zu erstellenden Dimensionen aus, und klicken Sie dann **auf Weiter**.  
  
    > [!NOTE]  
    >  Die Seite **Neue Dimensionen auswählen** wird angezeigt, wenn Tabellen geeignete Kandidaten für Dimensionstabellen wären und sie noch nicht von vorhandenen Dimensionen verwendet werden.  
  
7.  Wählen Sie auf der Seite **Fehlende Dimensionsschlüssel auswählen** einen Schlüssel für die Dimension aus, und klicken Sie dann **auf Weiter**.  
  
    > [!NOTE]  
    >  Die Seite **Fehlende Dimensionsschlüssel auswählen** wird angezeigt, wenn für die von Ihnen angegebenen Dimensionstabellen kein Schlüssel definiert wurde.  
  
8.  Geben Sie auf der Seite **Assistenten abschließen** einen Namen für den neuen Cube ein, und überprüfen Sie die Cubestruktur. Wenn Sie Änderungen vornehmen möchten, klicken Sie auf **Zurück**, andernfalls auf **Fertig stellen**.  
  
    > [!NOTE]  
    >  Sie können den Cube-Designer verwenden, nachdem Sie den Cube-Assistenten vervollständigt haben, um den Cube zu konfigurieren. Sie können außerdem den Dimensions-Designer zum Hinzufügen, Entfernen und Konfigurieren von Attributen und Hierarchien in den von Ihnen erstellten Dimensionen verwenden.  
  
  
