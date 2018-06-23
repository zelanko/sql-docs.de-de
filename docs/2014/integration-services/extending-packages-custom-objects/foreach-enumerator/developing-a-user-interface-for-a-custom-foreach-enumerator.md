---
title: Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten ForEach-Enumerator | Microsoft-Dokumentation
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
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2429f6b055484925470e61f65c73ce6ee13dbc4d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159617"
---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a>Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten ForEach-Enumerator
  Nachdem Sie die Implementierung der Eigenschaften und Methoden der Basisklasse überschrieben haben, um benutzerdefinierte Funktionen bereitzustellen, möchten Sie vielleicht eine benutzerdefinierte Benutzeroberfläche für den Foreach-Enumerator erstellen. Wenn Sie keine individuelle Benutzeroberfläche erstellen, können die Benutzer den neuen benutzerdefinierten ForEach-Enumerator nur über das Eigenschaftenfenster konfigurieren.  
  
 Erstellen Sie in einem benutzerdefinierten Benutzeroberflächenprojekt oder einer entsprechenden Assembly eine Klasse, die den <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI> implementiert. Diese Klasse wird von „System.Windows.Forms.UserControl“ abgeleitet, das typischerweise zur Erstellung eines zusammengesetzten Steuerelements als Host für andere Windows Forms-Steuerelemente verwendet wird. Das von Ihnen erstellte Steuerelement wird im Bereich **Enumeratorkonfiguration** der Registerkarte **Auflistung** des **Foreach-Schleifen-Editors** angezeigt.  
  
> [!IMPORTANT]  
>  Nach dem Signieren und Erstellen der benutzerdefinierten Benutzeroberfläche und der Installation im globalen Assemblycache wie in [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md) (Erstellen, Bereitstellen und Debuggen von benutzerdefinierten Objekten) beschrieben müssen Sie den vollqualifizierten Namen dieser Klasse in der <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> bereitstellen.  
  
## <a name="coding-the-user-interface-control-class"></a>Codieren der Benutzeroberflächen-Steuerelementklasse  
  
### <a name="initializing-the-user-interface"></a>Initialisieren der Benutzeroberfläche  
 Sie überschreiben die <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A>-Methode, um Verweise auf das Hostobjekt sowie die im Paket definierten Auflistungen von Verbindungs-Managern und Variablen zwischenzuspeichern.  
  
### <a name="setting-properties-on-the-user-interface-control"></a>Festlegen von Eigenschaften für das Benutzeroberflächensteuerelement  
 Die UserControl-Klasse, von der die Benutzeroberflächenklasse abgeleitet wird, dient zur Verwendung als zusammengesetztes Steuerelement zum Hosten anderer Windows Forms-Steuerelemente. Da diese Klasse als Host für andere Steuerelemente dient, können Sie Ihre benutzerdefinierte Oberfläche durch Ziehen und Ablegen von Steuerelementen entwerfen. Sie können diese wie bei jeder Windows Forms-Anwendung anordnen, ihre Eigenschaften festlegen und zur Ausführungszeit auf ihre Ereignisse reagieren.  
  
### <a name="saving-settings"></a>Speichern von Einstellungen  
 Sie überschreiben die <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A>-Methode, um die vom Benutzer festgelegten Werte beim Beenden des Editors aus den Steuerelementen in die Eigenschaften des Enumerators zu kopieren.  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben Sie mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines benutzerdefinierten Foreach-Enumerators](creating-a-custom-foreach-enumerator.md)   
 [Codieren eines benutzerdefinierten Foreach-Enumerators](coding-a-custom-foreach-enumerator.md)  
  
  