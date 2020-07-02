---
title: srv_message_handler (API für erweiterte gespeicherte Prozeduren)
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_message_handler
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
author: rothja
ms.author: jroth
ms.openlocfilehash: 5841cdb3f57c0c4b6e33737d8c08b3ff0437e800
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85756732"
---
# <a name="srv_message_handler-extended-stored-procedure-api"></a>srv_message_handler (API für erweiterte gespeicherte Prozeduren)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Ruft den installierten Meldungshandler für die API für erweiterte gespeicherte Prozeduren auf. Diese Funktion wird normalerweise verwendet, um [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus einer erweiterten gespeicherten Prozedur aufzurufen, um einen von der erweiterten gespeicherten Prozedur definierten Fehler in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlerprotokoll Datei oder im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendungsprotokoll zu protokollieren.  
  
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
  
 *errornum*  
 Eine von der erweiterten gespeicherten Prozedur definierte Fehlernummer. Diese Zahl muss zwischen 50.001 und 2.147.483.647 liegen.  
  
 *severity*  
 Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Standardwert für den Schweregrad des Fehlers. Diese Zahl ist ein Wert zwischen 0 und 24.  
  
 *state*  
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
  
## <a name="returns"></a>Gibt zurück  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Über die **srv_message_handler**-Funktion kann eine erweiterte gespeicherte Prozedur mit der zentralisierten Fehlerprotokollierung und den Berichterstellungsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integriert werden. Für Ereignisse in erweiterten gespeicherten Prozeduren können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warnungen festgelegt werden, die dann vom SQL Server-Agent überwacht werden.  
  
 Wenn die Fehlermeldung zu lang ist, wird sie bei 412 Byte abgeschnitten.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://msdn.microsoft.com/security/).  
  
  
