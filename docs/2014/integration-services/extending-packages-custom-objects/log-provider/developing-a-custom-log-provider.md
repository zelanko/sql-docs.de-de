---
title: Entwickeln eines benutzerdefinierten Protokollanbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2bd0daad6090b5ad55144f74d513c7c698783700
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85427417"
---
# <a name="developing-a-custom-log-provider"></a>Entwickeln eines benutzerdefinierten Protokollanbieters
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] bietet umfassende Protokollierungsfunktionen, mit denen Sie bei der Paketausführung auftretende Ereignisse erfassen können. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] beinhaltet eine Palette von Protokollanbietern, über die Protokolle erstellt und in Formaten wie XML, in Textform, in Datenbanken oder im Windows-Ereignisprotokoll gespeichert werden können. Sollten die Protokollanbieter und die angebotenen Ausgabeformate Ihre Anforderungen nicht vollständig erfüllen, können Sie benutzerdefinierte Protokollanbieter erstellen.

 Zum Erstellen eines benutzerdefinierten Protokollanbieters müssen Sie eine Klasse erstellen, die von der <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>-Basisklasse erbt, das <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>-Attribut auf die neue Klasse anwenden und die Hauptmethoden und -eigenschaften der Basisklasse, einschließlich der <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A>-Eigenschaft und der <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>-Methode, überschreibt.

## <a name="in-this-section"></a>In diesem Abschnitt
 In diesem Abschnitt wird beschrieben, wie Sie einen benutzerdefinierten Protokollanbieter erstellen, konfigurieren und den entsprechenden Code schreiben.

 [Erstellen eines benutzerdefinierten Protokoll Anbieters](creating-a-custom-log-provider.md) Beschreibt, wie die Klassen für ein benutzerdefiniertes Protokoll Anbieter Projekt erstellt werden.

 [Codieren eines benutzerdefinierten Protokoll Anbieters](coding-a-custom-log-provider.md) Beschreibt, wie ein benutzerdefinierter Protokoll Anbieter durch Überschreiben der Methoden und Eigenschaften der Basisklasse implementiert wird.

 [Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten Protokoll Anbieter](developing-a-user-interface-for-a-custom-log-provider.md) Benutzerdefinierte Benutzeroberflächen für benutzerdefinierte Protokoll Anbieter werden in nicht unterstützt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .

## <a name="related-topics"></a>Verwandte Themen

### <a name="information-common-to-all-custom-objects"></a>Informationen, die für alle benutzerdefinierten Objekte gelten
 Informationen zu allen Arten benutzerdefinierter Objekte, die Sie in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] erstellen können, finden Sie in den folgenden Themen:

 [Entwickeln von benutzerdefinierten Objekten für Integration Services](../developing-custom-objects-for-integration-services.md) Beschreibt die grundlegenden Schritte zum Implementieren aller Typen von benutzerdefinierten Objekten für [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .

 Beibehalten von [benutzerdefinierten Objekten](../persisting-custom-objects.md) Beschreibt die benutzerdefinierte Persistenz und erläutert, wann dies notwendig ist.

 Entwickeln, bereitstellen [und Debuggen von benutzerdefinierten Objekten](../building-deploying-and-debugging-custom-objects.md) Beschreibt die Techniken zum entwickeln, signieren, bereitstellen und Debuggen von benutzerdefinierten Objekten.

### <a name="information-about-other-custom-objects"></a>Informationen zu anderen benutzerdefinierten Objekten
 Informationen zu den anderen Typen benutzerdefinierter Objekte, die Sie in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] erstellen können, finden Sie in den folgenden Themen:

 [Entwickeln eines benutzerdefinierten](../task/developing-a-custom-task.md) Tasks Erläutert, wie benutzerdefinierte Tasks programmiert werden.

 [Entwickeln eines benutzerdefinierten Verbindungs-Managers](../connection-manager/developing-a-custom-connection-manager.md) Erläutert, wie benutzerdefinierte Verbindungs-Manager programmiert werden.

 [Entwickeln eines benutzerdefinierten Foreach-Enumerators](../foreach-enumerator/developing-a-custom-foreach-enumerator.md) Erläutert, wie benutzerdefinierte Enumeratoren programmiert werden.

 [Entwickeln einer benutzerdefinierten Datenfluss Komponente](../data-flow/developing-a-custom-data-flow-component.md) Erläutert, wie benutzerdefinierte Datenfluss Quellen,-Transformationen und-Ziele programmiert werden.

![Integration Services Symbol (klein)](../../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.


