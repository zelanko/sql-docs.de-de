---
title: Mitglieder der SQLServerParameterMetaData | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f9ebb203-2013-4feb-94f5-494b7f098f9a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f3f0c6558416c3a5736d7e5ce9663c5f9a7190a0
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66773518"
---
# <a name="sqlserverparametermetadata-members"></a>SQLServerParameterMetaData-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Die folgenden Tabellen enthalten die Elemente, die von der [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
 Keine.  
  
## <a name="fields"></a>Felder  
 Keine.  
  
## <a name="inherited-fields"></a>Geerbte Felder  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|java.sql.ParameterMetaData|parameterModeIn, parameterModeInOut, parameterModeOut, parameterModeUnknown, parameterNoNulls, parameterNullable, parameterNullableUnknown|  
  
## <a name="methods"></a>Methoden  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|[getParameterClassName](../../../connect/jdbc/reference/getparameterclassname-method-sqlserverparametermetadata.md)|Ruft den vollqualifizierten Namen der Java-Klasse ab, deren Instanzen an die [setObject](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)-Methode der [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse übergeben werden sollen.|  
|[getParameterCount](../../../connect/jdbc/reference/getparametercount-method-sqlserverparametermetadata.md)|Ruft die Anzahl von Parametern im [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Objekt ab, für die dieses [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)-Objekt Informationen enthält.|  
|[getParameterMode](../../../connect/jdbc/reference/getparametermode-method-sqlserverparametermetadata.md)|Ruft den Modus des angegebenen Parameters ab.|  
|[getParameterType](../../../connect/jdbc/reference/getparametertype-method-sqlserverparametermetadata.md)|Ruft den SQL-Typ des angegebenen Parameters ab.|  
|[getParameterTypeName](../../../connect/jdbc/reference/getparametertypename-method-sqlserverparametermetadata.md)|Ruft den datenbankspezifischen Typnamen des angegebenen Parameters ab.|  
|[getPrecision](../../../connect/jdbc/reference/getprecision-method-sqlserverparametermetadata.md)|Ruft die Anzahl von Dezimalstellen für den angegebenen Parameter ab.|  
|[getScale](../../../connect/jdbc/reference/getscale-method-sqlserverparametermetadata.md)|Ruft für den angegebenen Parameter die Anzahl von Stellen hinter dem Dezimalzeichen ab.|  
|[isNullable](../../../connect/jdbc/reference/isnullable-method-sqlserverparametermetadata.md)|Ruft ab, ob im angegebenen Parameter NULL-Werte zulässig sind.|  
|[isSigned](../../../connect/jdbc/reference/issigned-method-sqlserverparametermetadata.md)|Ruft ab, ob es sich bei den Werten für den angegebenen Parameter um Zahlen mit Vorzeichen handeln kann.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerParameterMetaData-Klasse](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
