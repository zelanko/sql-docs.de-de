---
title: Verweisen auf Assemblys in einer RDL-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- RDL [Reporting Services], referencing assemblies
- referencing custom assemblies
- custom assemblies [Reporting Services], referencing
- Report Definition Language, referencing assemblies
- report definition files [Reporting Services]
ms.assetid: 9a48e552-7d47-4243-9be1-894990c506d9
caps.latest.revision: 35
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 129e8d896dac89451af46873f97bcdc6074d016f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047559"
---
# <a name="referencing-assemblies-in-an-rdl-file"></a>Verweisen auf Assemblys in einer RDL-Datei
  Um die Verwendung von Assemblys mit benutzerdefiniertem Code in Berichtsdefinitionsdateien zu unterstützen, sind zwei RDL-Elemente (Report Definition Language) in der RDL-Spezifikation enthalten: das **CodeModules** und das **Classes**-Element.  
  
 Mithilfe des **CodeModules**-Elements kann in Berichtsausdrücken auf Assemblys mit verwaltetem Code verwiesen werden. **CodeModules** ist ein Element auf oberster Ebene, das den Verweis auf die Assembly enthält, mit der in Ihren Berichtsdefinitionsdateien spezialisierte Funktionen aufgerufen werden. Ein Eintrag in einer Berichtsdefinition, der die Verwendung einer benutzerdefinierten Assembly unterstützt, kann folgendermaßen aussehen:  
  
```  
<CodeModules>  
   <CodeModule>CurrencyConversion, Version=1.0.1363.31103, Culture=neutral, PublicKeyToken=null</CodeModule>  
</CodeModules>  
```  
  
 Statt <xref:System.Reflection.Assembly.Load%2A> aus benutzerdefiniertem Code aufzurufen, registrieren Sie die benutzerdefinierten Assemblys entweder, indem Sie der RDL-Datei die **CodeModule**-Elemente manuell hinzufügen, oder mithilfe der Registerkarte **Verweise** im Dialogfeld **Berichtseigenschaften**. Weitere Informationen finden Sie unter [Benutzerdefinierter Code und Assemblyverweise in Ausdrücken in Berichts-Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 Das **Classes**-Element unterstützt die Verwendung von Instanzelementen in einer Berichtsdefinition. **Classes** ist ein Element der obersten Ebene, das einen Verweis auf den Klassen- und einen Instanznamen enthält. Ein Eintrag in einer Berichtsdefinition, der die Verwendung von Instanzelementen unterstützt, kann folgendermaßen aussehen:  
  
```  
<Classes>  
   <Class>  
      <ClassName>CurrencyConversion.DollarCurrencyConversion</ClassName>  
      <InstanceName>m_myDollarConversion</InstanceName>  
   </Class>  
</Classes>  
```  
  
 Weitere Informationen finden Sie unter [Zugriff auf benutzerdefinierte Assemblys über Ausdrücke](accessing-custom-assemblies-through-expressions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](using-custom-assemblies-with-reports.md)  
  
  