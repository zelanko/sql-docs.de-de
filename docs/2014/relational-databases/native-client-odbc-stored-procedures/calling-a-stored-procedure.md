---
title: Aufrufen einer gespeicherten Prozedur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- ODBC, stored procedures
- stored procedures [ODBC], calling
- SQL Server Native Client ODBC driver, stored procedures
- ODBC CALL escape sequence
- escape sequences [SQL Server]
- CALL statement
ms.assetid: d13737f4-f641-45bf-b56c-523e2ffc080f
author: rothja
ms.author: jroth
ms.openlocfilehash: c6fa704e45e4e85b479ae8a40a3e567bea1ec5e9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049724"
---
# <a name="calling-a-stored-procedure"></a>Aufrufen von gespeicherten Prozeduren
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt sowohl die ODBC-Rückruf-Escapesequenz als auch die [!INCLUDE[tsql](../../includes/tsql-md.md)] [Execute](/sql/t-sql/language-elements/execute-transact-sql) -Anweisung zum Ausführen gespeicherter Prozeduren. die ODBC-Rückruf Sequenz ist die bevorzugte Methode Mithilfe der ODBC-Syntax kann eine Anwendung die Rückgabecodes von gespeicherten Prozeduren abrufen. Zudem wurde der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber für die Verwendung eines ursprünglich zum Senden von Remoteprozeduraufrufen (RPC) zwischen Computern, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführen, entwickelten Protokolls optimiert. Dieses RPC-Protokoll erhöht die Leistung, indem es einen Großteil der Parameterverarbeitung und Anweisungsauswertung auf dem Server überflüssig macht.  
  
> [!NOTE]  
>  Beim Aufrufen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherter Prozeduren mit benannten Parametern mit ODBC (Weitere Informationen finden Sie unter [Binden von Parametern anhand des Namens (benannte Parameter)](https://go.microsoft.com/fwlink/?LinkID=209721)) müssen die Parameternamen mit dem \@ Zeichen "" beginnen. Dies ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifische Einschränkung. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODCB-Treiber erzwingt diese Einschränkung strenger als die MDAC (Microsoft Data Access Components).  
  
 Die ODBC CALL-Escapesequenz für das Aufrufen einer Prozedur lautet wie folgt:  
  
 {[**? =**]**aufrufen**_procedure_name_[([*Parameter*] [**,**[*Parameter*]]...)]}  
  
 wobei *procedure_name* den Namen einer Prozedur angibt und *Parameter* einen Prozedur Parameter angibt. Benannte Parameter werden nur in Anweisungen mit ODBC CALL-Escapesequenz unterstützt.  
  
 Eine Prozedur kann 0 (null) oder mehr Parameter haben. Sie kann außerdem einen Wert zurückgeben (wie durch die optionale Parametermarkierung ?= am Anfang der Markierung angegeben). Wenn es sich bei einem Parameter um einen Eingabe- oder einen Eingabe-/Ausgabeparameter handelt, kann ein Literalwert oder eine Parametermarkierung verwendet werden. Wenn es sich bei dem Parameter um einen Ausgabeparameter handelt, muss eine Parametermarkierung verwendet werden, da die Ausgabe unbekannt ist. Parameter Markierungen müssen mit [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) gebunden werden, bevor die Prozedur aufrufen-Anweisung ausgeführt wird.  
  
 Eingabe- und Eingabe-/Ausgabeparameter müssen in Prozeduraufrufen nicht angegeben werden. Wenn eine Prozedur mit Klammern aber ohne Parameter aufgerufen wird, weist der Treiber die Datenquelle an, für den ersten Parameter den Standardwert zu verwenden. Beispiel:  
  
 {**call** _procedure_name_**()**} abrufen  
  
 Wenn die Prozedur keine Parameter aufweist, kann bei der Prozedur ein Fehler auftreten. Wenn eine Prozedur ohne Klammern aufgerufen wird, sendet der Treiber keine Parameterwerte. Beispiel:  
  
 {**call** _procedure_name_} abrufen  
  
 Literalwerte können in Prozeduraufrufen für Eingabe- und Eingabe-/Ausgabeparameter angegeben werden. Die Prozedur InsertOrder weist beispielsweise fünf Parameter auf. Beim folgenden Aufruf von InsertOrder ist der erste Parameter nicht angegeben, für den zweiten Parameter ist ein Literalwert angegeben und für den dritten, vierten und fünften Parameter wird eine Parametermarkierung verwendet. (Parameter werden sequenziell nummeriert und beginnen mit dem Wert 1.)  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}  
```  
  
 Wenn ein Parameter nicht angegeben wird, muss das Komma dennoch gesetzt werden, damit dieser Parameter von anderen Parametern abgegrenzt wird. Wenn ein Eingabe- oder ein Eingabe-/Ausgabeparameter ausgelassen wird, verwendet die Prozedur den Standardwert des Parameters. Eine weitere Möglichkeit, den Standardwert eines Eingabe- oder eines Eingabe-/Ausgabeparameters anzugeben, besteht darin, den Wert des an den Parameter gebundenen Längen-/Indikatorpuffers auf SQL_DEFAULT_PARAM festzulegen oder das DEFAULT-Schlüsselwort zu verwenden.  
  
 Wenn ein Eingabe-/Ausgabeparameter ausgelassen oder ein Literalwert für den Parameter angegeben wird, verwirft der Treiber den Ausgabewert. Entsprechend verwirft der Treiber den Rückgabewert, wenn die Parametermarkierung für den Rückgabewert einer Prozedur ausgelassen wird. Wenn eine Anwendung den Parameter des Rückgabewerts für eine Prozedur angibt, die keinen Wert zurückgibt, legt der Treiber den Wert des an den Parameter gebundenen Längen-/Indikatorpuffers auf SQL_NULL_DATA fest.  
  
## <a name="delimiters-in-call-statements"></a>Trennzeichen in CALL-Anweisungen  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt außerdem standardmäßig eine für die ODBC { CALL }-Escapesequenz spezifische Kompatibilitätsoption. Der Treiber akzeptiert nur CALL-Anweisungen mit einem Satz doppelter Anführungszeichen zum Trennen des gesamten Namens der gespeicherten Prozedur:  
  
```  
{ CALL "master.dbo.sp_who" }  
```  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber akzeptiert darüber hinaus auch standardmäßig CALL-Anweisungen, die den ISO-Regeln gehorchen und bei denen jeder Bezeichner in doppelten Anführungszeichen steht:  
  
```  
{ CALL "master"."dbo"."sp_who" }  
```  
  
 Beim Ausführen der Standardeinstellungen unterstützt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber bei Bezeichnern mit Zeichen, die durch den ISO-Standard nicht als gültige Zeichen in Bezeichnern angegeben sind, jedoch keine Form von Bezeichnern mit Anführungszeichen. Beispielsweise kann der Treiber nicht auf eine gespeicherte Prozedur mit dem Namen **"My. proc"** zugreifen, indem eine-Anweisung mit Bezeichnern in Anführungszeichen verwendet wird:  
  
```  
{ CALL "MyDB"."MyOwner"."My.Proc" }  
```  
  
 Diese Anweisung wird vom Treiber wie folgt interpretiert:  
  
```  
{ CALL MyDB.MyOwner.My.Proc }  
```  
  
 Der Server löst einen Fehler aus, dass kein Verbindungs Server mit dem Namen **mydb** vorhanden ist.  
  
 Das Problem tritt nicht auf, wenn Bezeichner in Klammern verwendet werden. Dann wird diese Anweisung richtig interpretiert:  
  
```  
{ CALL [MyDB].[MyOwner].[My.Table] }  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen gespeicherter Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
