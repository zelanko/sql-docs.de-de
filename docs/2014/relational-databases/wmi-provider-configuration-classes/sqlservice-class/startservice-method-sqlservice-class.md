---
title: StartService-Methode (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartService method
ms.assetid: 83dfb6bd-dbd5-45d8-aad2-a11926317f91
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d0a425bda3d32f19aca5be09dbb8ba4b7b6ac899
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911717"
---
# <a name="startservice-method-sqlservice-class"></a>StartService-Methode (SqlService-Klasse)
  Versucht, den Dienst zu starten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.StartService()  
  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlService-Klassenobjekt](sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32-Wert, der den einen der folgenden Startstatus angibt:  
  
 0  
 Erfolg. Die Anforderung wurde akzeptiert.  
  
 1  
 Nicht unterstützt. Die Anforderung wird nicht unterstützt.  
  
 2  
 Zugriff verweigert. Der Benutzer hatte keinen entsprechenden Zugriff.  
  
 3  
 Abhängige Dienste werden ausgeführt. Der Dienst kann nicht beendet werden, da andere ausgeführte Dienste davon abhängig sind.  
  
 4  
 Ungültige Dienstkontrolle. Der angeforderte Steuerungscode ist nicht gültig, oder es ist für den Dienst nicht akzeptabel.  
  
 5  
 Die Steuerung kann vom Dienst nicht angenommen werden. Der angeforderte Steuerungscode kann nicht an den Dienst gesendet werden, weil der Status des Diensts (Win32_BaseService:State) 0, 1 oder 2 lautet.  
  
 6  
 Der Dienst ist nicht aktiv. Der Dienst wurde nicht gestartet.  
  
 7  
 Timeout bei der Dienstanforderung. Der Dienst hat auf die Startanforderung nicht rechtzeitig reagiert.  
  
 8  
 Unbekannter Fehler. Beim Starten des Diensts ist ein unbekannter Fehler aufgetreten.  
  
 9  
 Der Pfad wurde nicht gefunden. Der Verzeichnispfad zur ausführbaren Dienstdatei wurde nicht gefunden.  
  
 10  
 Der Dienst wird bereits ausgeführt. Der Dienst wird schon ausgeführt.  
  
 11  
 Die Dienstdatenbank ist gesperrt. Die Datenbank zum Hinzufügen eines neuen Diensts ist gesperrt.  
  
 12  
 Die Dienstabhängigkeit wurde gelöscht. Eine Abhängigkeit, von der dieser Dienst abhängt, wurde aus dem System entfernt.  
  
 13  
 Dienstabhängigkeitenfehler. Der Dienst hat den Dienst nicht gefunden, der von einem abhängigen Dienst benötigt wird.  
  
 14  
 Der Dienst ist deaktiviert. Der Dienst wurde vom System deaktiviert.  
  
 15  
 Fehler bei der Dienstanmeldung. Der Dienst hat nicht die richtige Authentifizierung, um im System ausgeführt zu werden.  
  
 16  
 Der Dienst ist zum Löschen markiert. Der Dienst wird aus dem System entfernt.  
  
 17  
 Der Dienst besitzt keinen Thread. Es gibt keinen Ausführungsthread für den Dienst.  
  
 18  
 Ringabhängigkeitsstatus. Es gibt Ringabhängigkeiten beim Starten des Diensts.  
  
 19  
 Doppelter Name. Es wird ein Dienst unter dem gleichen Namen ausgeführt.  
  
 20  
 Ungültiger Name. Im Namen des Dienstes sind ungültige Zeichen vorhanden.  
  
 21  
 Ungültige Parameter. Ungültige Parameter wurden an den Dienst übergeben.  
  
 22  
 Ungültiges Dienstkonto. Das Konto, unter dem dieser Dienst ausgeführt werden soll, ist nicht gültigt oder verfügt nicht über die Berechtigung zum Ausführen des Diensts.  
  
 23  
 Der Dienst ist bereits vorhanden. Der Dienst ist in der Datenbank der im System verfügbaren Dienste vorhanden.  
  
 24  
 Der Dienst wurde bereits angehalten. Der Dienst ist im System derzeitig angehalten.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
