---
title: Verwenden von gespeicherten Prozeduren mit einem Rückgabestatus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b126e95-8458-41d6-af37-fc6662859f19
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d4077f11e28bc382976eb3da441cfd42a24a567f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797141"
---
# <a name="using-a-stored-procedure-with-a-return-status"></a>Verwenden von gespeicherten Prozeduren mit einem Rückgabestatus

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Bei einer aufrufbaren gespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozedur handelt es sich um eine Prozedur, die einen Status- oder Ergebnisparameter zurückgibt. Damit wird normalerweise ermittelt, ob die gespeicherte Prozedur erfolgreich ausgeführt wurde oder fehlgeschlagen ist. Die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] bietet die [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) -Klasse, die Sie verwenden können, um diese Art von gespeicherter Prozedur aufzurufen und zum Verarbeiten der Daten, die zurückgegeben.

Wenn Sie diese Art von gespeicherter Prozedur mit dem JDBC-Treiber aufrufen, müssen Sie die `call`-SQL-Escapesequenz zusammen mit der Methode [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) der Klasse [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) verwenden. Die Syntax für die `call`-Escapesequenz mit einem Rückgabestatusparameter lautet wie folgt:

`{[?=]call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Weitere Informationen zu SQL-Escapesequenzen, finden Sie unter [mithilfe von SQL-Escapesequenzen](../../connect/jdbc/using-sql-escape-sequences.md).

Geben Sie die Rückgabestatusparameter beim Erstellen der `call`-Escapesequenz mit dem Fragezeichen (?) an. das als Platzhalter für den Parameterwert fungiert, der von der gespeicherten Prozedur zurückgegeben wird. Um einen Wert für einen Rückgabestatusparameter anzugeben, müssen Sie vor dem Ausführen der gespeicherten Prozedur den Datentyp des Parameters mit der Methode [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) der Klasse „SQLServerCallableStatement“ angeben.

> [!NOTE]  
> Wenn der JDBC-Treiber mit einer SQL Server-Datenbank verwendet wird, handelt es sich bei dem Wert, der in der Methode „registerOutParameter“ für den Rückgabestatusparameter angegeben wird, immer um einen Integer-Wert. Dies können Sie mit dem Datentyp java.sql.Types.INTEGER angeben.

Wenn Sie an die Methode „registerOutParameter“ einen Wert für einen Rückgabestatusparameter übergeben, müssen Sie darüber hinaus nicht nur den Datentyp für den Parameter angeben, sondern auch die ordinale Position des Parameters im Aufruf der gespeicherten Prozedur. Für den Rückgabestatusparameter ist die ordinale Position immer 1, da es sich immer um den ersten Parameter im Aufruf der gespeicherten Prozedur handelt. Obwohl die Klasse „SQLServerCallableStatement“ die Verwendung des Namens eines Parameters zum Angeben dieses Parameters unterstützt, können Sie für Rückgabestatusparameter nur die Ordnungspositionsnummer verwenden.

Erstellen Sie als Beispiel die folgende Prozedur in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank:

```sql
CREATE PROCEDURE CheckContactCity  
   (@cityName CHAR(50))  
AS  
BEGIN  
   IF ((SELECT COUNT(*)  
   FROM Person.Address  
   WHERE City = @cityName) > 1)  
   RETURN 1  
ELSE  
   RETURN 0  
END  
```

Diese gespeicherte Prozedur gibt abhängig davon, ob der im cityName-Parameter angegebene Ort in der Person.Address-Tabelle gefunden wurde, den Statuswert 1 oder 0 zurück.

Im folgenden Beispiel werden eine offene Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben und die gespeicherte Prozedur „CheckContactCity“ mit der Methode [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) aufgerufen:

[!code[JDBC#UsingSprocWithReturnStatus1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_1_1.java)]

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Anweisungen mit gespeicherten Prozeduren](../../connect/jdbc/using-statements-with-stored-procedures.md)
