---
title: Unterstützung von XML-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 32b7217e-1f0c-473d-9a45-176daa81584e
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d97499468b1d44f761b01888312e1ba97c722c7c
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785751"
---
# <a name="supporting-xml-data"></a>Unterstützen von XML-Daten
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst einen **XML**-Datentyp, mit dem Sie XML-Dokumente und -Fragmente in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank speichern können. Der **XML**-Datentyp ist ein integrierter Datentyp in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und ähnelt in einigen Punkten anderen integrierten Typen wie **int** und **varchar**. Wie andere integrierte Typen können Sie den **XML**-Datentyp beim Erstellen einer Tabelle als Spaltentyp, als Variablentyp, als Parametertyp oder als Funktionsrückgabetyp bzw. in CAST- und CONVERT-Funktionen von [!INCLUDE[tsql](../../includes/tsql-md.md)] verwenden. Im JDBC-Treiber kann der **XML**-Datentyp als Zeichenfolgen-, Bytearray-, Stream-, CLOB-, BLOB- oder SQLXML-Objekt zugeordnet werden. Die Standardzuordnung ist als Zeichenfolge.  
  
 Der JDBC-Treiber bietet Unterstützung für die JDBC 4.0-API, in der die SQLXML-Schnittstelle eingeführt wird. Die SQLXML-Schnittstelle definiert Methoden für die Interaktion mit und die Bearbeitung von XML-Daten. Die **SQLXML** ist ein JDBC 4.0-Datentyp und entspricht dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Xml** -Datentyp. Um den SQLXML-Datentyp in der Anwendung verwenden zu können, müssen Sie daher den Klassenpfad so festlegen, dass die Datei „sqljdbc4.jar“ enthalten ist. Wenn die Anwendung beim Zugriff auf das SQLXML-Objekt und seine Methoden versucht, „sqljdbc3.jar“ zu verwenden, wird eine Ausnahme ausgelöst.  
  
> [!IMPORTANT]  
>  Die XML-Daten werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] immer überprüft, bevor sie in der Datenbankspalte gespeichert werden. Anwendungen können den **SQLXML**-Datentyp verwenden, da er vom JDBC-Treiber automatisch dem **XML**-Datentyp zugeordnet wird. Die **SQLXML**-Unterstützung wird durch „sqljdbc4.jar“ bereitgestellt. Finden Sie unter [Systemanforderungen für JDBC Driver](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md) für die Liste der vom unterstützten JRE-Versionen der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 Die Themen in diesem Abschnitt beschreiben die SQLXML-Schnittstelle und die Programmierung für den **SQLXML**-Datentyp mit den Methoden der JDBC-API.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|und Beschreibung|  
|-----------|-----------------|  
|[SQLXML-Schnittstelle](../../connect/jdbc/sqlxml-interface.md)|Beschreibt die SQLXML-Schnittstelle und ihre Methoden.|  
|[Programmieren mit SQLXML](../../connect/jdbc/programming-with-sqlxml.md)|Beschreibt, wie mithilfe der API-Methoden von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] XML-Daten mit dem Java-Datentyp **SQLXML** in einer relationalen Datenbank gespeichert bzw. aus einer relationalen Datenbank abgerufen werden. Außerdem sind Informationen über die Typen von SQLXML-Objekten und eine Liste wichtiger Richtlinien und Einschränkungen für die Verwendung von SQLXML-Objekten enthalten.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Grundlegendes zu den Datentypen in JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
