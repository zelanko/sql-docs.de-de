---
title: Synchronize21-Methode (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Synchronize21 method [ADO]
ms.assetid: 6b35f136-9d9a-4bdd-8144-67decfd3c4e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d2fd1ab1363cc56d2029a0d6ecb4218c518dac4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63155235"
---
# <a name="synchronize21-method-rds"></a>Synchronize21-Methode (RDS)
Synchronisieren Sie das angegebene Recordset, mit der Datenbank, die durch die Verbindungszeichenfolge für die Verwendung mit ADO 2.1 angegeben.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Synchronize21(ConnectionString As String, HandlerString As String, lSynchronizeOptions As Long, ppRecordset As Object, pStatusArray)  
```  
  
#### <a name="parameters"></a>Parameter  
 *ConnectionString*  
 Eine Zeichenfolge verwendet, um mit dem OLE DB-Anbieter hergestellt, in dem die Anforderung gesendet werden. Wenn ein Handler verwendet wird, kann der Handler bearbeiten oder Ersetzen Sie die Verbindungszeichenfolge.  
  
 *HandlerString*  
 Die Zeichenfolge identifiziert, den Handler, der mit dieser Ausführung verwendet werden. Die Zeichenfolge besteht aus zwei Teilen. Der erste Teil enthält den Namen (ProgID) des Handlers verwendet werden. Der zweite Teil der Zeichenfolge enthält Argumente, die an den Handler übergeben werden. Wie die Argumentzeichenfolge interpretiert wird, ist bestimmten Handler. Die beiden Teile sind durch die erste Instanz eines Kommas in der Zeichenfolge getrennt. Die Zeichenfolge mit Befehlsargumenten kann zusätzliche Kommas enthalten. Die Argumente sind optional.  
  
 *lSynchronizeOptions*  
 Eine Bitmaske der Synchronisierungsoptionen.  
  
 1 =*UpdateTransact* Aktualisierungen der Datenbank in einer Transaktion zusammengefasst werden. Die Transaktion wird abgebrochen, wenn eines der Updates ein Fehler auftritt.  
  
 2 =*RefreshWithUpdate* bewirkt, dass Zeile Status zurückgegeben werden, wenn weder *aktualisieren* noch *RefreshConflicts* festgelegt ist.  
  
 4 =*aktualisieren* das Recordset mit aktuellen Daten aus der Datenbank aktualisiert wird. Ausstehende Updates werden nicht auf die Datenbank übertragen. Wenn dieses Bit nicht festgelegt ist, wird das Recordset nicht aktualisiert, und alle ausstehenden Updates an die Datenbank gesendet werden.  
  
 8 =*RefreshConflicts* keine Zeilen mit ausstehenden Änderungen aktualisiert. Zeilen, die Fehler beim Aktualisieren werden mit aktuellen Daten aus der Datenbank aktualisiert.  
  
 *ppRecordset*  
 Ein Zeiger auf einen Zeiger auf das Recordset synchronisiert werden.  
  
 *pStatusArray*  
 Synchronisieren eine Variante, die ein sicheres Array der Status der Zeile für die betroffenen Zeilen zurückgibt. Nicht festgelegt, wenn keine der folgenden Optionen für die Synchronisierung festgelegt werden: *RefreshWithUpdate*, *aktualisieren* und *RefreshConflicts*.  
  
## <a name="remarks"></a>Hinweise  
 Die *HandlerString* Parameter kann null sein. Was in diesem Fall geschieht, hängt davon ab, wie die RDS-Server konfiguriert ist. Eine Zeichenfolge Handler "MSDFMAP.handler" gibt an, dass der Handler für Microsoft bereitgestellt (Msdfmap.dll) verwendet werden soll. Eine Zeichenfolge Handler "MASDFMAP.handler,sample.ini" gibt an, dass der Handler für Msdfmap.dll verwendet werden soll und das Argument "sample.ini" an den Ereignishandler übergeben werden sollen. Klicken Sie dann interpretiert Msdfmap.dll das Argument als eine Richtung auf die sample.ini verwenden, um die Verbindungs- und Zeichenfolgen zu überprüfen.  
  
> [!NOTE]
>  Die **Synchronize21** Methode ist einfach eine Version von der [synchronisieren Methode (RDS)](../../../ado/reference/rds-api/synchronize-method-rds.md). Müssen Sie verwenden die **synchronisieren** Methode für die Kommunikation mit ADO 2.1 die **Synchronize21** -Methode stattdessen aufgerufen werden kann. Die Funktionen des die **synchronisieren** -Methode in der ADO 2.5 und höher stellen eine Obermenge der Funktionen für die gleiche Methode in ADO 2.1 bereitgestellt.  
  
## <a name="applies-to"></a>Gilt für  
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


