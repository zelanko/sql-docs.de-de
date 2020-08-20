---
description: MDX-Datendefinition – CREATE ACTION
title: Create action-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7132c28e93dbc11eee1c5a4e4d53126f280fa74a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494903"
---
# <a name="mdx-data-definition---create-action"></a>MDX-Datendefinition – CREATE ACTION


  Erstellt eine Aktion, die einem Cube, einer Dimension, einer Hierarchie oder einem untergeordneten Objekt zugeordnet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CREATE ACTION CURRENTCUBE | Cube_Name  
   .Action_Name <action body>  
<action body> ::=   
FOR   
        CUBE   
    | Hierarchy_Name [MEMBERS]   
    | Level_Name [MEMBERS]   
    | CELLS   
    | SET }   
      AS 'MDX_Expression'   
        [, TYPE = '  
              { URL   
            | HTML   
            | STATEMENT   
               | DATASET   
            | ROWSET   
            | COMMANDLINE   
               | PROPRIETARY }   
         ']  
   [ , INVOCATION = 'INTERACTIVE | ON_OPEN | BATCH ' ]  
   [ , APPLICATION = String_Expression ]  
   [ , DESCRIPTION = String_Expression ]  
   [ , CAPTION = 'MDX_Expression' ]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Eine gültige Zeichenfolge, die einen Cubenamen bereitstellt.  
  
 *Action_ Name*  
 Eine gültige Zeichenfolge, die den Namen der zu erstellenden Aktion bereitstellt.  
  
 *Hierarchy_ Name*  
 Eine gültige Zeichenfolge, die einen Hierarchienamen bereitstellt.  
  
 *Level_ Name*  
 Eine gültige Zeichenfolge, die einen Ebenennamen bereitstellt.  
  
 *Member_ Name*  
 Eine gültige Zeichenfolge, die einen Elementnamen oder Elementschlüssel bereitstellt.  
  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck.  
  
 *String_Expression*  
 Ein gültiger Zeichenfolgenausdruck.  
  
## <a name="remarks"></a>Bemerkungen  
 Es ist möglich, dass Clientanwendungen unsichere Aktionen erstellen und ausführen oder unsichere Funktionen verwenden. Um diese Situationen zu vermeiden, verwenden Sie die Eigenschaft **Sicherheitsoptionen** . Weitere Informationen finden Sie im Abschnitt zur Safety Options-Eigenschaft.  
  
> [!NOTE]  
>  Diese Anweisung wird nur aus Gründen der Abwärtskompatibilität bereitgestellt. Aktionen, die in neu sind [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , z. b. Drillthrough-oder Berichts Aktionen, werden nicht unterstützt.  
  
## <a name="action-types"></a>Aktions Typen  
 In der folgenden Tabelle werden die verschiedenen Typen von Aktionen beschrieben, die in verfügbar sind [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
|Aktionstyp|BESCHREIBUNG|  
|-----------------|-----------------|  
|**URL**|Die zurückgegebene Aktionszeichenfolge ist eine URL, die mit einem Internetbrowser geöffnet werden sollte.<br /><br /> Hinweis: Wenn diese Aktion nicht mit oder beginnt `https://` `https://` , ist die Aktion für den Browser nicht verfügbar, es sei denn, **SafetyOptions** ist auf **DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL**festgelegt.|  
|**HTML**|Die zurückgegebene Aktionszeichenfolge ist ein HTML-Skript. Die Zeichenfolge sollte in einer Datei gespeichert werden, und die Datei sollte mit einem Internetbrowser gerendert werden. In diesem Fall kann ein ganzes Skript als Teil des generierten HTML-Codes ausgeführt werden.|  
|**An**|Die zurückgegebene Aktions Zeichenfolge ist eine Anweisung, die ausgeführt werden muss, indem die **ICommand:: SetText** -Methode eines Befehls Objekts auf die Zeichenfolge festgelegt und die **ICommand:: Execute**-Methode aufgerufen wird. Wenn der Befehl nicht erfolgreich ausgeführt werden kann, wird ein Fehler zurückgegeben.|  
|**DataSet**|Die zurückgegebene Aktions Zeichenfolge ist eine MDX-Anweisung, die ausgeführt werden muss, indem die **ICommand:: SetText** -Methode eines Befehls Objekts auf die Zeichenfolge festgelegt und die **ICommand:: Execute** -Methode aufgerufen wird. Die angeforderte Schnittstellen-ID (IID) sollte " **IDataset**" lauten. Der Befehl ist erfolgreich, wenn ein Dataset erstellt wurde. Die Clientanwendung sollte dem Benutzer das Durchsuchen des zurückgegebenen Datasets ermöglichen.|  
|**Rowset**|Ähnlich wie beim **DataSet**muss die Client Anwendung jedoch eine IID von **IRowset**anfordern, anstatt eine IID von **IDataset**anzufordern. Der Befehl ist erfolgreich, wenn ein Rowset erstellt wurde. Die Clientanwendung sollte dem Benutzer das Durchsuchen des zurückgegebenen Rowsets ermöglichen.|  
|**CommandLine**|Die Clientanwendung sollte die Aktionszeichenfolge ausführen. Die Zeichenfolge stellt eine Befehlszeile dar.|  
|**Tä**|Eine Clientanwendung sollte die Aktion nicht anzeigen oder ausführen, wenn sie nicht über benutzerdefiniertes, nicht generisches Wissen über die bestimmte Aktion verfügt. Proprietäre Aktionen werden nur dann an die Client Anwendung zurückgegeben, wenn die Client Anwendung diese explizit anfordert, indem die entsprechende Einschränkung für die **APPLICATION_NAME**festgelegt wird.|  
  
## <a name="invocation-types"></a>Aufruftypen  
 In der folgenden Tabelle sind die verschiedenen Typen von Aufrufen beschrieben, die in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] zur Verfügung stehen. Der Aufruftyp wird nur von der Clientanwendung verwendet, um zu bestimmen, wann die Aktion aufgerufen werden soll. Das Aufrufverhalten der Aktion selbst wird nicht durch den Aufruftyp bestimmt.  
  
|Aufruftyp|Beschreibung|  
|---------------------|-----------------|  
|**Interaktive**|Die Aktion sollte von der Clientanwendung durch Benutzerinteraktion aufgerufen werden.|  
|**ON_OPEN**|Die Aktion sollte von der Clientanwendung aufgerufen werden, wenn das Zielobjekt geöffnet wird. Dieser Aufruftyp ist zurzeit nicht implementiert.|  
|**Batches**|Die Aktion sollte von der Clientanwendung aufgerufen werden, wenn das Zielobjekt an einem von der Clientanwendung bestimmten Batchvorgang beteiligt ist. Dieser Aufruftyp ist zurzeit nicht implementiert.|  
  
### <a name="scope"></a>`Scope`  
 Jede Aktion ist für einen bestimmten Cube definiert und besitzt einen eindeutigen Namen innerhalb des Cubes. Eine Aktion kann für einen der Bereiche in der folgenden Tabelle gelten.  
  
 Cubebereich  
 Die Aktion ist unabhängig von bestimmten Dimensionen, Elementen oder Zellen. Beispiel: "Launch terminal emulation for AS/400 production system".  
  
 Dimensionsbereich  
 Die Aktion gilt für eine bestimmte Dimension. Diese Aktionen sind nicht von einer bestimmten Auswahl von Ebenen oder Elementen abhängig.  
  
 Ebenenbereich  
 Die Aktion gilt für eine bestimmte Dimensionsebene. Diese Aktionen sind nicht von einer bestimmten Auswahl eines Elements in dieser Dimension abhängig.  
  
 Element Bereich  
 Die Aktion gilt für bestimmte Ebenenelemente.  
  
 Zellenbereich  
 Die Aktion gilt nur für bestimmte Zellen.  
  
 Mengenbereich  
 Die Aktion gilt nur für eine Menge. Der Name " **Action Parameterset**" ist für die Verwendung durch die Anwendung innerhalb des Ausdrucks der Aktion reserviert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Daten Definitions Anweisungen &#40;MDX-&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
