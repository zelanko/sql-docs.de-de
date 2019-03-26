---
title: Wiederverwenden von Paketobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- GUID regenerating [Integration Services]
- reusing packages
- templates [Integration Services]
- copying packages
- regenerating package GUID
ms.assetid: 08f723bf-15b5-44bd-9a46-04e8781bfbfb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: cd98db30045ad2c6658d6d7d2df0b98f1abed192
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58272352"
---
# <a name="reuse-of-package-objects"></a>Wiederverwenden von Paketobjekten
  Pakete schließen häufig Funktionalität ein, die Sie wiederverwenden möchten. Wenn Sie beispielsweise eine Reihe von Tasks erstellt haben, möchten Sie möglicherweise die Elemente zusammen als eine Gruppe wiederverwenden, oder Sie möchten ein einzelnes Element, z. B. einen Verbindungs-Manager, den Sie in einem anderen [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt erstellt haben, wiederverwenden.  
  
## <a name="copy-and-paste"></a>Kopieren und Einfügen  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] und der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer unterstützen das Kopieren und Einfügen von Paketobjekten. Hierzu zählen Ablaufsteuerungselemente, Datenflusselemente und Verbindungs-Manager. Elemente können aus einem Projekt bzw. aus einem Paket kopiert und in ein anderes Projekt bzw. Paket eingefügt werden. Wenn die Lösung mehrere Projekte enthält, können Sie von einem Projekt in ein anderes kopieren. Dabei können die einzelnen Projekte unterschiedlichen Typs sein.  
  
 Wenn eine Lösung mehrere Pakete enthält, können Sie diverse Kopier- und Einfügevorgänge zwischen diesen durchführen. Dabei können sich die Pakete im selben oder in einem anderen [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt befinden. Paketobjekte können jedoch von anderen Objekten abhängig sein, durch die sie erst gültig sind. Beispielsweise verwendet der Task SQL ausführen einen Verbindungs-Manager, den Sie ebenfalls kopieren müssen, um den Task ordnungsgemäß ausführen zu können. Des Weiteren erfordern einige Paketobjekte das Vorhandensein eines bestimmten Objekts im Paket. Ohne dieses Objekt können die kopierten Objekte nicht erfolgreich in das Paket eingefügt werden. Sie können beispielsweise einen Datenfluss in ein Paket nur dann einfügen, wenn mindestens ein Datenflusstask im Paket vorhanden ist.  
  
 Möglicherweise müssen Sie ein und dieselben Pakete mehrere Male kopieren. Sie können diesen Kopiervorgang umgehen, indem Sie diese Pakete als Vorlagen festlegen und beim Erstellen neuer Pakete verwenden.  
  
 Beim Kopieren eines Paketobjekts weist [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] der **ID** -Eigenschaft des neuen Objekts automatisch einen neuen GUID zu und aktualisiert die Eigenschaft **Name** .  
  
 Das Kopieren von Variablen ist nicht möglich. Wenn ein Objekt, z. B. ein Task, Variablen verwendet, müssen die Variablen im Zielpaket neu erstellt werden. Wenn Sie allerdings das gesamte Paket kopieren, werden die Variablen des Pakets ebenfalls kopiert.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Kopieren von Paketobjekten](../integration-services/copy-package-objects.md)  
  
-   [Kopieren von Projektelementen](https://msdn.microsoft.com/library/1606c54d-20f9-49f3-a4ef-caad83a772aa)  
  
-   [Speichern eines Pakets als Paketvorlage](https://msdn.microsoft.com/library/efe66cec-3933-4f6e-8d35-fe3d300de66c)  
  
  
