---
title: srv_message_handler (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_message_handler
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f597aa6c9ba9759b606501b0bd72a2166b1805e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63127407"
---
# <a name="srv_message_handler-extended-stored-procedure-api"></a>srv_message_handler (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Ruft den installierten Meldungshandler für die API für erweiterte gespeicherte Prozeduren auf. Diese Funktion wird normalerweise verwendet, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um aus einer erweiterten gespeicherten Prozedur aufzurufen, um einen von der erweiterten gespeicherten Prozedur definierten Fehler in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Fehlerprotokoll Datei oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] im Windows-Anwendungsprotokoll zu protokollieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_message_handler (  
SRV_PROC *  
srvproc  
,  
int  
errornum  
,  
BYTE   
severity  
,  
BYTE  
state  
,  
int  
oserrnum  
,  
char *  
errtext  
,  
int  
errtextlen  
,  
char *  
oserrtext  
,  
int  
oserrtextlen  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist. Der *srvproc*-Parameter enthält Informationen, mit denen die Daten und die Kommunikation zwischen der Anwendung und dem Client verwaltet werden.  
  
 *ERRORNUM*  
 Eine von der erweiterten gespeicherten Prozedur definierte Fehlernummer. Diese Zahl muss zwischen 50.001 und 2.147.483.647 liegen.  
  
 *zunehmen*  
 Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Standardwert für den Schweregrad des Fehlers. Diese Zahl ist ein Wert zwischen 0 und 24.  
  
 *Land*  
 Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Statuswert für den Fehler.  
  
 *oserrnum*  
 Die Nummer des Betriebssystemfehlers. Dieses Argument wird ignoriert.  
  
 *errtext*  
 Die Beschreibung des Fehlers der erweiterten gespeicherten Prozedur *errornum*.  
  
 *errtextlen*  
 Die Länge der Fehlerzeichenfolge der erweiterten gespeicherten Prozedur *errtext*.  
  
 *oserrtext*  
 Die Beschreibung des Betriebssystemfehlers *oserrnum*. Dieses Argument wird ignoriert.  
  
 *oserrtextlen*  
 Die Länge der Zeichenfolge des Betriebssystemfehlers *oserrtext*.  
  
## <a name="returns"></a>Rückgabe  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Bemerkungen  
 Über die **srv_message_handler**-Funktion kann eine erweiterte gespeicherte Prozedur mit der zentralisierten Fehlerprotokollierung und den Berichterstellungsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integriert werden. Für Ereignisse in erweiterten gespeicherten Prozeduren können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warnungen festgelegt werden, die dann vom SQL Server-Agent überwacht werden.  
  
 Wenn die Fehlermeldung zu lang ist, wird sie bei 412 Byte abgeschnitten.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
