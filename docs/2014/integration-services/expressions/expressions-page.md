---
title: Seite Ausdrücke | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eb12bb684753a5d965054e361f8b0b23ebf7802d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150470"
---
# <a name="expressions-page"></a>Seite Ausdrücke
  Mithilfe der Seite **Ausdrücke** können Sie Eigenschaftsausdrücke bearbeiten und auf die Dialogfelder **Eigenschaftsausdrucks-Editor** und **Eigenschaftsausdrucks-Generator** zugreifen.  
  
 Eigenschaftsausdrücke aktualisieren die Werte von Eigenschaften, wenn das Paket ausgeführt wird. Eigenschaftsausdrücke können mit den Eigenschaften von Paketen, Tasks, Containern, Verbindungs-Managern sowie einigen Datenflusskomponenten verwendet werden. Die Ausdrücke werden ausgewertet und ihre Ergebnisse werden anstelle der Werte verwendet, auf die Sie die Eigenschaften festgelegt haben, als Sie das Paket und die Paketobjekte konfiguriert haben. Die Ausdrücke können Variablen und die Funktionen und Operatoren enthalten, die die Ausdruckssprache bereitstellt. Beispielsweise können Sie die Betreffzeile für den Task Mail senden generieren, indem Sie den Wert einer Variablen, die die Zeichenfolge "Weather forecast for " enthält, und die zurückgegebenen Ergebnisse der GETDATE()-Funktion zu der Zeichenfolge "Weather forecast for 4/5/2006" verketten.  
  
 Weitere Informationen zum Schreiben von Ausdrücken und zum Verwenden von Eigenschaftsausdrücken finden Sie unter [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) und [Verwenden von Eigenschaftsausdrücken in Paketen](use-property-expressions-in-packages.md).  
  
## <a name="options"></a>Tastatur  
 **Ausdrücke (...)**  
 Klicken Sie auf die Auslassungspunkte (...), um das Dialogfeld **Eigenschaftsausdrucks-Editor** zu öffnen. Weitere Informationen finden Sie unter [Property Expressions Editor](property-expressions-editor.md).  
  
 **\<Eigenschaftsname>**  
 Klicken Sie auf die Schaltfläche mit den drei Punkten, um das Dialogfeld **Ausdrucks-Generator** zu öffnen. Weitere Informationen finden Sie unter [Expression Builder](expression-builder.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Integrationsdienste &#40;SSIS&#41; Variablen](../integration-services-ssis-variables.md)   
 [Systemvariablen](../system-variables.md)   
 [Integration Services-Ausdrücke &#40;SSIS&#41;](integration-services-ssis-expressions.md)  
  
  
