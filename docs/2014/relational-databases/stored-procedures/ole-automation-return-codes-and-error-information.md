---
title: Rückgabecodes und Fehlerinformationen der OLE-Automatisierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- return codes [SQL Server]
- OLE Automation [SQL Server], return codes
- OLE Automation [SQL Server], errors
ms.assetid: 9696fb05-e9e8-4836-b359-d4de0be0eeb2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 57614db23c50236c6af783d7f913c897fda3e8df
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414019"
---
# <a name="ole-automation-return-codes-and-error-information"></a>Rückgabecodes und Fehlerinformationen der OLE-Automatisierung
  Der OLE-Automatisierung gespeicherten Systemprozeduren geben eine `int` -Rückgabecode zurück, das HRESULT, der von der zugrunde liegenden OLE-Automatisierungsvorgang zurückgegeben wird. Ein HRESULT von 0 zeigt eine erfolgreiche Ausführung an. Ein HRESULT ungleich NULL ist ein OLE-Fehlercode im hexadezimalen Format 0 x 800*Nnnnn*, als ein `int` Wert in einer gespeicherten Prozedur Rückgabecode weist dem Format 214*Nnnnnnn*.  
  
 Übergabe eines ungültigen Objektnamens (SQLDMO. XYZZY) an die Sp_OACreate bewirkt, dass das Verfahren zum Zurückgeben einer `int` HRESULT von 2147221005, was im hexadezimalen Format 0x800401f3 entspricht.  
  
 Sie können `CONVERT(binary(4), @hresult)` verwenden, um ein `int`-HRESULT in einen `binary`-Wert zu konvertieren. Die Verwendung von `CONVERT(char(10), CONVERT(binary(4), @hresult))` ergibt jedoch eine nicht lesbare Zeichenfolge, da jedes Byte von HRESULT in ein einzelnes ASCII-Zeichen konvertiert wird. Sie können die folgende gespeicherte HexToChar-Beispielprozedur verwenden, konvertieren eine `int` HRESULT, das eine `char` Wert, der eine lesbare hexadezimale Zeichenfolge enthält.  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS(SELECT name FROM sys.objects  
          WHERE name = N'dbo.sp_HexToChar')  
    DROP PROCEDURE HexToChar;  
GO  
CREATE PROCEDURE dbo.sp_HexToChar  
    @BinValue varbinary(255),  
    @HexCharValue nvarchar(255) OUTPUT  
AS  
    DECLARE @CharValue nvarchar(255);  
    DECLARE @Position int;  
    DECLARE @Length int;  
    DECLARE @HexString nchar(16);  
    SELECT @CharValue = N'0x';  
    SELECT @Position = 1;  
    SELECT @Length = DATALENGTH(@BinValue);  
    SELECT @HexString = N'0123456789ABCDEF';  
    WHILE (@Position <= @Length)  
    BEGIN  
        DECLARE @TempInt int;  
        DECLARE @FirstInt int;  
        DECLARE @SecondInt int;  
        SELECT @TempInt = CONVERT(int, SUBSTRING(@BinValue,@Position,1));  
        SELECT @FirstInt = FLOOR(@TempInt/16);  
        SELECT @SecondInt = @TempInt - (@FirstInt*16);  
        SELECT @CharValue = @CharValue +  
            SUBSTRING(@HexString, @FirstInt+1, 1) +  
            SUBSTRING(@HexString, @SecondInt+1, 1);  
        SELECT @Position = @Position + 1;  
    END  
    SELECT @HexCharValue = @CharValue;  
GO  
DECLARE @BinVariable varbinary(35);  
DECLARE @CharValue nvarchar(35);  
  
SET @BinVariable = 123456;  
  
EXECUTE dbo.sp_HexToChar  
    @binvalue = @BinVariable,  
    @HexCharValue = @CharValue OUTPUT;  
  
SELECT @BinVariable AS BinaryValue,  
    @CharValue AS CharacterRep;  
GO  
```  
  
 Sie können auch die folgende gespeicherte **sp_displayoaerrorinfo** -Beispielprozedur verwenden, um Fehlerinformationen der OLE-Automatisierung anzuzeigen, wenn eine dieser Prozeduren einen HRESULT-Rückgabecode ungleich null zurückgibt. Diese gespeicherte Beispielprozedur verwendet `HexToChar`.  
  
```  
CREATE PROCEDURE dbo.sp_DisplayOAErrorInfo  
    @Object int,  
    @HResult int  
AS  
    DECLARE @Output nvarchar(255);  
    DECLARE @HRHex nchar(10);  
    DECLARE @HR int;  
    DECLARE @Source nvarchar(255);  
    DECLARE @Description nvarchar(255);  
    PRINT N'OLE Automation Error Information';  
    EXEC HexToChar @HResult, @HRHex OUT;  
    SELECT @Output = N'  HRESULT: ' + @HRHex;  
    PRINT @Output;  
    EXEC @HR = sp_OAGetErrorInfo  
        @Object,  
        @Source OUT,  
        @Description OUT;  
    IF @HR = 0  
    BEGIN  
        SELECT @Output = N'  Source: ' + @Source;  
        PRINT @Output;  
        SELECT @Output = N'  Description: '  
               + @Description;  
        PRINT @Output;  
    END  
    ELSE  
    BEGIN  
       PRINT N' sp_OAGetErrorInfo failed.';  
       RETURN;  
    END  
GO  
```  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [sp_OAGetErrorInfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql)  
  
  
