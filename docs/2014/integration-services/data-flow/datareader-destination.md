---
title: DataReader-Ziel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 40cfe5d99c33eb19d415f204173005a64bde7855
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432257"
---
# <a name="datareader-destination"></a>DataReader-Ziel
  Das DataReader-Ziel macht die Daten in einem Datenfluss mithilfe der `DataReader`-Schnittstelle von ADO.NET verfügbar. Die Daten können dann von anderen Anwendungen verwendet werden. Beispielsweise können Sie die Datenquelle eines [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichts so konfigurieren, dass das Ergebnis der Ausführung eines [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakets verwendet wird. Dazu erstellen Sie einen Datenfluss, der das DataReader-Ziel implementiert.  
  
 Informationen zum programmgesteuerten Zugriff auf Werte im DataReader-Ziel und zum programmgesteuerten Lesen dieser Werte finden Sie unter [Laden der Ausgabe eines lokalen Pakets](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).  
  
## <a name="configuration-of-the-datareader-destination"></a>Konfiguration des DataReader-Ziel  
 Sie können einen Timeoutwert für das DataReader-Ziel angeben und konfigurieren, ob das Ziel einen Fehler erzeugen soll, wenn ein Timeout auftritt. Ein Timeout tritt auf, wenn die Anwendung nicht innerhalb der angegebenen Zeit Daten anfordert.  
  
 Das DataReader-Ziel hat eine Eingabe. Eine Fehlerausgabe wird nicht unterstützt.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften des DataReader-Ziels](datareader-destination-custom-properties.md)  
  
 Weitere Informationen zum Festlegen der Eigenschaften finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md).  
  
  
