---
title: Parameterinfo (IntelliSense)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Parameter Info option [IntelliSense]
- stored function parameter completion [Intellisense]
- language references [SQL Server]
- IntelliSense [SQL Server], Parameter Info option
ms.assetid: 56c2aac9-c65c-4679-b62c-d9f689876dde
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d5668216e971c0e7c68e75f395699254ec61c109
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75253743"
---
# <a name="parameter-info-intellisense"></a>Parameterinfo (IntelliSense)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Die Option [!INCLUDE[msCoName](../../includes/msconame-md.md)] Parameter Info **von** IntelliSense öffnet eine Parameterliste, die Informationen über die Anzahl, Namen und Typen der Parameter enthält, die für eine Funktion oder gespeicherte Prozedur erforderlich sind. Der fett formatierte Parameter gibt den nächsten Parameter an, der beim Eingeben einer Funktion oder gespeicherten Prozedur erforderlich ist.  
  
 Die Parameterliste wird auch für geschachtelte Funktionen angezeigt. Wenn Sie eine Funktion als Parameter für eine andere Funktion eingeben, werden in der Parameterliste die Parameter für die innere Funktion angezeigt. Wenn die Parameterliste der inneren Funktion vollständig ist, werden in der Parameterliste anschließend die Parameter der äußeren Funktion angezeigt.  
  
#### <a name="to-view-parameter-info-for-functions-or-stored-procedures"></a>So zeigen Sie Parameterinfo für Funktionen oder gespeicherte Prozeduren an  
  
1.  Geben Sie nach dem Namen einer Funktion wie gewohnt eine öffnende Klammer ein, um die Parameterliste zu öffnen. Wenn Sie den Namen einer gespeicherten Prozedur eingegeben haben, geben Sie wie gewohnt ein Leerzeichen ein, um Informationen zu den Prozedurparametern abzurufen.  
  
     IntelliSense zeigt die vollständige Deklaration für die Funktion oder die Parameter für eine gespeicherte Prozedur in einem Popupfenster direkt unter der Einfügemarke an. Der erste Parameter in der Liste wird fett formatiert angezeigt.  
  
2.  Beim Eingeben der Parameter ändert sich die Fettformatierung, um den nächsten Parameter anzugeben, den Sie eingeben müssen.  
  
3.  Drücken Sie zu einem beliebigen Zeitpunkt die ESC-TASTE, um die Liste zu schließen, oder fahren Sie mit der Eingabe fort, bis die Funktion abgeschlossen ist.  
  
     Wenn Sie für eine Funktion die schließende Klammer eingeben, schließen Sie auch die Parameterliste.  
  
#### <a name="to-manually-start-parameter-info"></a>So starten Sie Parameterinfo manuell  
  
1.  Wählen Sie im Menü **Bearbeiten** **IntelliSense** und anschließend **Parameterinfo**aus.  
  
2.  Drücken Sie die Tastenkombination STRG+UMSCHALT+LEERZEICHEN.  
  
 Weitere Informationen finden Sie unter [Konfigurieren von IntelliSense &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/configure-intellisense-sql-server-management-studio.md).  
  
> [!NOTE]  
>  Die Option **Parameter Info** ist nur für den [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor und den XML-Abfrage-Editor verfügbar.  
  
  
