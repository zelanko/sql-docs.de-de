---
title: Wiederverwenden von Paketobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 086f3d6808668003fa03d79fcbf2911c18b3c0da
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964560"
---
# <a name="reuse-of-package-objects"></a>Wiederverwenden von Paketobjekten
  Pakete schließen häufig Funktionalität ein, die Sie wiederverwenden möchten. Wenn Sie beispielsweise eine Reihe von Tasks erstellt haben, möchten Sie möglicherweise die Elemente zusammen als eine Gruppe wiederverwenden, oder Sie möchten ein einzelnes Element, z. B. einen Verbindungs-Manager, den Sie in einem anderen [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt erstellt haben, wiederverwenden.  
  
## <a name="copy-and-paste"></a>Kopieren und Einfügen  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] und der [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer unterstützen das Kopieren und Einfügen von Paketobjekten. Hierzu zählen Ablaufsteuerungselemente, Datenflusselemente und Verbindungs-Manager. Elemente können aus einem Projekt bzw. aus einem Paket kopiert und in ein anderes Projekt bzw. Paket eingefügt werden. Wenn die Lösung mehrere Projekte enthält, können Sie von einem Projekt in ein anderes kopieren. Dabei können die einzelnen Projekte unterschiedlichen Typs sein.  
  
 Wenn eine Lösung mehrere Pakete enthält, können Sie diverse Kopier- und Einfügevorgänge zwischen diesen durchführen. Dabei können sich die Pakete im selben oder in einem anderen [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt befinden. Paketobjekte können jedoch von anderen Objekten abhängig sein, durch die sie erst gültig sind. Beispielsweise verwendet der Task SQL ausführen einen Verbindungs-Manager, den Sie ebenfalls kopieren müssen, um den Task ordnungsgemäß ausführen zu können. Des Weiteren erfordern einige Paketobjekte das Vorhandensein eines bestimmten Objekts im Paket. Ohne dieses Objekt können die kopierten Objekte nicht erfolgreich in das Paket eingefügt werden. Sie können beispielsweise einen Datenfluss in ein Paket nur dann einfügen, wenn mindestens ein Datenflusstask im Paket vorhanden ist.  
  
 Möglicherweise müssen Sie ein und dieselben Pakete mehrere Male kopieren. Sie können diesen Kopiervorgang umgehen, indem Sie diese Pakete als Vorlagen festlegen und beim Erstellen neuer Pakete verwenden.  
  
 Beim Kopieren eines Paketobjekts weist [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] der `ID`-Eigenschaft des neuen Objekts automatisch einen neuen GUID zu und aktualisiert die `Name`-Eigenschaft.  
  
 Das Kopieren von Variablen ist nicht möglich. Wenn ein Objekt, z. B. ein Task, Variablen verwendet, müssen die Variablen im Zielpaket neu erstellt werden. Wenn Sie allerdings das gesamte Paket kopieren, werden die Variablen des Pakets ebenfalls kopiert.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Kopieren von Paketobjekten](../../2014/integration-services/copy-package-objects.md)  
  
-   [Kopieren von Projektelementen](../../2014/integration-services/copy-project-items.md)  
  
-   [Speichern eines Pakets als Paketvorlage](../../2014/integration-services/save-a-package-as-a-package-template.md)  
  
  
