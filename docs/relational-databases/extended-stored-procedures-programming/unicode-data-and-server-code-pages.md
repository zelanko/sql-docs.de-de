---
title: Unicode-Daten und Server-Codepages | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- metadata [SQL Server], stored procedures
- Unicode [SQL Server], extended stored procedures
- extended stored procedures [SQL Server], metadata
ms.assetid: 52310260-a892-4b27-ad2e-bf164b98ee80
author: rothja
ms.author: jroth
ms.openlocfilehash: f32929b9cd5d2f69ae4ffbb8d13f7ec09d9972ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064271"
---
# <a name="unicode-data-and-server-code-pages"></a>Unicode-Daten und Server-Codepages
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Verwenden Sie stattdessen die CLR-Integration.  
  
 Die API für erweiterte gespeicherte Prozeduren ist für die Verarbeitung von Unicode-Daten aktiviert, jedoch nicht für Unicode-Metadaten. Die Unicode-Direktive #define hat keinerlei Wirkung auf die API für erweiterte gespeicherte Prozeduren.  
  
 Für alle Metadaten, die von der API für erweiterte gespeicherte Prozeduren zurückgegeben oder durch Ihre Anwendung mit erweiterten gespeicherten Prozeduren für die API bereitgestellt werden, wird angenommen, dass sie im Multibytecodepageformat des Servers vorliegen. Die Standard Codepage einer API-Serveranwendung für erweiterte gespeicherte Prozeduren ist die ANSI-Codepage des Computers, auf dem die Anwendung ausgeführt wird. dieser kann durch Aufrufen von **srv_pfield** abgerufen werden, wobei der Feld Parameter auf SRV_SPROC_CODEPAGE festgelegt ist.  
  
 Wenn für Ihre mit der API für erweiterte gespeicherte Prozeduren erstellte Anwendung Unicode aktiviert ist, müssen Sie die Unicode-Metadaten für Spaltennamen, Fehlermeldungen usw. in Multibytedaten konvertieren, bevor Sie die Daten an die API für erweiterte gespeicherte Prozeduren übergeben.  
  
## <a name="example"></a>Beispiel  
 Die folgende erweiterte gespeicherte Prozedur stellt ein Beispiel für die beschriebenen Unicode-Konvertierungen bereit. Beachten Sie dabei Folgendes:  
  
-   Spaltendaten werden als Unicode-Daten an **srv_describe** weitergegeben, da die Spalte als SRVNVARCHAR beschrieben wird.  
  
-   Metadaten des Spaltennamens werden als Multibytedaten an **srv_describe** übermittelt.  
  
     Die erweiterte gespeicherte Prozedur ruft **srv_pfield** auf, wobei der Feld Parameter auf SRV_SPROC_CODEPAGE festgelegt ist, um die Multibytezeichen-Codepage von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu erhalten.  
  
-   Fehlermeldungen werden als Multibytedaten an **srv_sendmsg** übermittelt.  
  
    ```  
    __declspec(dllexport) RETCODE proc1 (SRV_PROC *srvproc)  
    {  
        #define MAX_COL_NAME_LEN 25  
        #define MAX_COL_DATA_LEN 50  
        #define MAX_ERR_MSG_LEN 250  
        #define MAX_SERVER_ERROR 20000  
        #define XP_ERROR_NUMBER MAX_SERVER_ERROR+1  
  
        int retval;  
        UINT serverCodePage;  
        CHAR *szServerCodePage;  
  
        WCHAR unicodeColumnName[MAX_COL_NAME_LEN];  
        CHAR multibyteColumnName[MAX_COL_NAME_LEN];  
  
        WCHAR unicodeColumnData[MAX_COL_DATA_LEN];  
  
        WCHAR unicodeErrorMessage[MAX_ERR_MSG_LEN];  
        CHAR  multibyteErrorMessage[MAX_ERR_MSG_LEN];  
  
        lstrcpyW (unicodeColumnName, L"column1");  
        lstrcpyW (unicodeColumnData, L"column1 data");  
        lstrcpyW (unicodeErrorMessage, L"No Error!");  
  
        // Obtain server code page.  
        //  
        szServerCodePage = srv_pfield (srvproc, SRV_SPROC_CODEPAGE, NULL);      
        if (NULL != szServerCodePage)  
            serverCodePage = atol(szServerCodePage);  
        else   
        {   // Problem situation exists.  
            srv_senddone(srvproc, (SRV_DONE_ERROR | SRV_DONE_MORE), 0, 0);  
            return 1;  
        }  
  
        // Convert column name for Unicode to multibyte using the   
        // server code page.  
        //  
        retval = WideCharToMultiByte(    
            serverCodePage,                 // code page  
            0,                              // default  
            unicodeColumnName,              // wide-character string  
            -1,                             // string is null terminated  
            multibyteColumnName,            // address of buffer for new  
                                            //   string  
            sizeof (multibyteColumnName),   // size of buffer  
            NULL, NULL);  
  
        if (0 == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"Conversion to multibyte  
            failed.");  
            goto Error;  
        }  
  
        retval = srv_describe (srvproc, 1, multibyteColumnName,  
        SRV_NULLTERM,   
          SRVNVARCHAR, MAX_COL_DATA_LEN*sizeof(WCHAR), // destination  
            SRVNVARCHAR, lstrlenW(unicodeColumnData)*sizeof(WCHAR),  
            unicodeColumnData); //source  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_describe failed.");  
            goto Error;  
        }  
  
       retval = srv_sendrow(srvproc);  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_sendrow failed.");  
            goto Error;  
        }  
  
        retval = srv_senddone (srvproc, SRV_DONE_MORE|SRV_DONE_COUNT, 0, 1);  
        if (FAIL == retval)  
        {  
            lstrcpyW (unicodeErrorMessage, L"srv_senddone failed.");  
            goto Error;  
        }  
  
        return 0;  
    Error:  
        // convert error message from Unicode to multibyte.  
        retval = WideCharToMultiByte(    
            serverCodePage,                 // code page  
            0,                              // default  
            unicodeErrorMessage,            // wide-character string  
            -1,                             // string is null terminated  
            multibyteErrorMessage,          // address of buffer for new  
                                            //   string  
            sizeof (multibyteErrorMessage), // size of buffer  
            NULL, NULL);  
  
    srv_sendmsg(srvproc, SRV_MSG_ERROR, XP_ERROR_NUMBER, SRV_INFO, 1,  
                NULL, 0, __LINE__,   
                multibyteErrorMessage,  
                SRV_NULLTERM);  
  
        srv_senddone(srvproc, (SRV_DONE_ERROR | SRV_DONE_MORE), 0, 0);  
  
        return 1;  
    }  
  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_wsendmsg &#40;API für erweiterte gespeicherte Prozeduren&#41;](../../relational-databases/extended-stored-procedures-reference/srv-wsendmsg-extended-stored-procedure-api.md)  
  
  
