---
title: Kommentare (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 26a529d6eb15997ccb48ad25d8d4fcb11cd2ddfb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68071056"
---
# <a name="comments-dmx"></a>Kommentare (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Kommentare in Data Mining-Erweiterungen (DMX) sind Text Zeichenfolgen im [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Programmcode, der nicht ausgeführt wird. Kommentare werden auch als Anmerkungen bezeichnet. Mit Kommentaren können Sie Code dokumentieren oder Teile einer DMX-Anweisung oder eines DMX-Skripts deaktivieren, wenn Sie den Code untersuchen.  
  
 Wenn Sie Programmcode mit Kommentaren dokumentieren, lässt sich der Code später einfacher pflegen. Mit Kommentaren können Sie bestimmte Informationen festhalten, so z. B. den Namen des Programms, den Namen des Entwicklers, der den Code geschrieben hat, und die Datumsangaben für wesentliche Codeänderungen. Außerdem können Sie Kommentare dazu verwenden, komplizierte Berechnungen oder eine Programmiermethode zu beschreiben.  
  
 Die folgenden Aussagen sind grundsätzliche Richtlinien für das Schreiben von Kommentaren:  
  
-   In Kommentaren können Sie sämtliche alphanumerischen Zeichen oder Symbole verwenden. 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ignoriert alle Zeichen in Kommentaren.  
  
-   Es gibt keine Längenbeschränkung für einen Kommentar innerhalb einer Anweisung oder eines Skripts. Ein Kommentar kann aus einer oder mehreren Zeilen bestehen.  
  
 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt die folgenden Zeichenkombinationen als Kommentarzeichen:  
  
-   **(doppelte Schrägstriche).** Verwenden Sie diese Kommentarzeichen, um einen Kommentar auf der gleichen Zeile wie auszuführender Code oder auch einen Kommentar auf einer eigenen Zeile zu schreiben. 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wertet den gesamten Text von den doppelten Schrägstrichen bis zum Ende der Zeile als Kommentar aus. Wenn Sie einen mehrzeiligen Kommentar erstellen möchten, verwenden Sie die doppelten Schrägstriche am Anfang jeder Kommentarzeile. Weitere Informationen zu diesem Kommentarzeichen finden Sie unter [Double Schrägstrich &#40;comment&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md).  
  
-   **--(doppelte Bindestriche).** Verwenden Sie diese Kommentarzeichen, um einen Kommentar auf der gleichen Zeile wie auszuführender Code oder auch einen Kommentar auf einer eigenen Zeile zu schreiben. 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wertet den gesamten Text von den doppelten Bindestrichen bis zum Ende der Zeile als Kommentar aus. Wenn Sie einen mehrzeiligen Kommentar erstellen möchten, verwenden Sie die doppelten Bindestriche am Anfang jeder Kommentarzeile. Weitere Informationen zu diesem Kommentarzeichen finden Sie unter [--&#40;comment&#41; &#40;DMX&#41; Summary](../dmx/comment-dmx-summary.md).  
  
-   **/\*... \*/(Schrägstrich/Sternchen-Zeichenpaare).** Verwenden Sie diese Kommentarzeichen, um einen Kommentar auf der gleichen Zeile wie der auszuführende Code, einen Kommentar auf einer eigenen Zeile oder Kommentare innerhalb des ausführbaren Codes zu schreiben. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]wertet alles vom geöffneten Kommentar Paar (/*) bis zum schließenden Kommentar Paar (\*/) als Teil des Kommentars aus. Wenn Sie einen mehrzeiligen Kommentar erstellen möchten, starten Sie den Kommentar mit dem öffnenden Kommentarzeichen\*Paar (/), und beenden Sie den Kommentar mit dem schließenden\*Kommentarzeichen Paar (/). Die Zeilen des Kommentars sollten keine anderen Kommentarzeichen enthalten. Weitere Informationen zu diesem Kommentarzeichen finden Sie unter [Schrägstrich-Stern &#40;comment&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Elemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Allgemeine Vorhersagefunktionen &#40;DMX-&#41;](../dmx/general-prediction-functions-dmx.md)   
 [Struktur und Verwendung von DMX-Vorhersage Abfragen](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Grundlegendes zur SELECT-Anweisung (DMX)](../dmx/understanding-the-dmx-select-statement.md)  
  
  
