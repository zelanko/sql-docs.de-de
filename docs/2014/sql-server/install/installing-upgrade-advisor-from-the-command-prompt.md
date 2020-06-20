---
title: Installieren von Upgrade Advisor von der Eingabeaufforderung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- command prompt [Upgrade Advisor]
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: a6841cc2-ca13-4b1c-9343-9e4d54312c3a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 738e1ef203f4c9c83e42c7d8255f82978465eadf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065293"
---
# <a name="installing-upgrade-advisor-from-the-command-prompt"></a>Installieren des Upgrade Advisors von der Eingabeaufforderung aus
  Sie können den Upgrade Advisor entweder mithilfe des Setup-Assistenten oder an der Eingabeaufforderung installieren. Die Eingabeaufforderung ermöglicht unbeaufsichtigte und automatisierte Installationen.  
  
## <a name="installation-syntax"></a>Installationssyntax  
 Die grundlegende Syntax für die Upgrade Advisor-Installation von der Eingabeaufforderung ist folgende:  
  
 `SQLUA.msi [options]`  
  
 In der folgenden Tabelle werden die gängigsten Optionen aufgelistet.  
  
|Argument|BESCHREIBUNG|  
|--------------|-----------------|  
|/q [n&#124;b&#124;r&#124;f]|Legt die Benutzeroberflächenebene fest:<br /><br /> n = keine Benutzeroberfläche<br /><br /> b = grundlegende Benutzeroberfläche (nur Status, keine Eingabeaufforderungen)<br /><br /> r = reduzierte Benutzeroberfläche (Dialogfeld am Ende der Installation)<br /><br /> f = Vollständige Benutzeroberfläche|  
|/L|Gibt Protokolldateioptionen an. Um alle Nachrichten in *log_file_name*zu protokollieren, verwenden Sie **-L \* v**_log_file_name_. Verwenden Sie log_file_name, um nur Fehlermeldungen zu protokollieren `-Le` *log_file_name*.|  
|ADDLOCAL = alle&#124; Remove = alle&#124;REINSTALL = ALL|Gibt an, dass der Upgrade Advisor installiert (ADDLOCAL), entfernt (REMOVE) oder neu installiert (REINSTALL) wird.|  
|UAINSTALLDIR=path|Installiert den Upgrade Advisor am von "path" angegebenen Speicherort.|  
  
## <a name="installation-examples"></a>Installationsbeispiele  
 Im folgenden Beispiel wird gezeigt, wie der Upgrade Advisor mithilfe der Eingabeaufforderung installiert wird:  
  
```  
SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 Sie können auch das Programm Msiexec verwenden, wenn Sie diesen Befehl ausführen:  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 Dies kann hilfreich sein, wenn Sie zusätzliche Installationsoptionen verwenden müssen.  
  
## <a name="removal-examples"></a>Beispiele für das Entfernen von Upgrade Advisor  
 Im folgenden Beispiel wird gezeigt, wie der Upgrade Advisor mithilfe der Eingabeaufforderung entfernt wird:  
  
```  
SQLUA.msi /qn REMOVE=ALL  
```  
  
 Sie können auch das Programm Msiexec verwenden, wenn Sie diesen Befehl ausführen:  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn REMOVE=ALL  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md)   
 [Voraussetzungen für den Upgrade Advisor](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
