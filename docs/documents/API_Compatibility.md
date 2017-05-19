##  2. API Compatibility

| Category | Function | SFM 3000/5000 | SFM 4000 | SFM 3500 | SFM 5500 | BE Pass | BE Smart |
| :------: | -------- | :-----------: | :------: | :------: | :------: | :-----: | :------: |
| Serial Comm. API | UF_InitCommPort | O | O | O | O | O | O |
|                  | UF_CloseCommPort | O | O | O | O | O | O |
|                  | UF_Reconnect | O | O | O | O | O | O |
|                  | UF_SetBaudrate | O | O | O | O | O | O |
|                  | UF_SetAsciiMode | O | O | O | O | O | O |
| Socket API | UF_InitSocket | O | O | O | O | O | O |
|            | UF_CloseSocket | O | O | O | O | O | O |
| Low-Level Packet API | UF_SendPacket | O | O | O | O | O | O |
|                      | UF_ReceivePacket | O | O | O | O | O | O |
|                      | UF_SendNetworkPacket | O | O | O | O | O | O |
|                      | UF_ReceiveNetworkPacket | O | O | O | O | O | O |
|                      | UF_SendRawData | O | O | O | O | O | O |
|                      | UF_ReceiveRawData | O | O | O | O | O | O |
|                      | UF_SendDataPacket | O | O | O | O | O | O |
|                      | UF_SetSendPacketCallback | O | O | O | O | O | O |
|                      | UF_SetReceivePacketCallback | O | O | O | O | O | O |
|                      | UF_SetSendDataPacketCallback | O | O | O | O | O | O |
|                      | UF_SetReceiveDataPacketCallback | O | O | O | O | O | O |
|                      | UF_SetSendRawDataCallback | O | O | O | O | O | O |
|                      | UF_SetReceiveRawDataCallback | O | O | O | O | O | O |
|                      | UF_SetDefaultPacketSize | O | O | O | O | O | O |
|                      | UF_GetDefaultPacketSize | O | O | O | O | O | O |
| General Command API | UF_Command | O | O | O | O | O | O |
|                     | UF_CommandEx | O | O | O | O | O | O |
|                     | UF_CommandSendData | O | O | O | O | O | O |
|                     | UF_CommandSendDataEx | O | O | O | O | O | O |
|                     | UF_Cancel | O | O | O | O | O | O |
|                     | UF_SetProtocol | O | O | O | O | O | O |
|                     | UF_GetProtocol | O | O | O | O | O | O |
|                     | UF_GetModuleID | O | O | O | O | O | O |
|                     | UF_SetGenericCommandTimeout | O | O | O | O | O | O |
|                     | UF_SetInputCommandTimeout | O | O | O | O | O | O |
|                     | UF_GetGenericCommandTimeout | O | O | O | O | O | O |
|                     | UF_GetInputCommandTimeout | O | O | O | O | O | O |
|                     | UF_SetNetworkDelay | O | O | O | O | O | O |
|                     | UF_GetNetworkDelay | O | O | O | O | O | O |
| Module API | UF_GetModuleInfo | O | O | O | O | O | O |
|            | UF_GetModuleString | O | O | O | O | O | O |
|            | UF_SearchModule | O | O | O | O | O | O |
|            | UF_SearchModuleID | O | O | O | O | O | O |
|            | UF_SearchModuleBySocket | O | O | O | O | O | O |
|            | UF_SearchModuleIDEx | O | O | O | O | O | O |
|            | UF_CalibrateSensor | O | O | O | O | O | O |
|            | UF_Upgrade | O | O | O | O | O | O |
|            | UF_Reset | O | O | O | O | O | O |
|            | UF_ PowerOff | X | O | X | X | X | X |
|            | UF_Lock | X | X | O | O | O | O |
|            | UF_Unlock | X | X | O | O | O | O |
|            | UF_ChangePassword | X | X | O | O | O | O |
| System Parameters API | UF_InitSysParameter | O | O | O | O | O | O |
|                       | UF_GetSysParameter | O | O | O | O | O | O |
|                       | UF_SetSysParameter | O | O | O | O | O | O |
|                       | UF_GetMultiSysParameter | O | O | O | O | O | O |
|                       | UF_SetMultiSysParameter | O | O | O | O | O | O |
|                       | UF_Save | O | O | O | O | O | O |
|                       | UF_SaveConfiguration | O | O | O | O | O | O |
|                       | UF_ReadConfigurationHeader | O | O | O | O | O | O |
|                       | UF_LoadConfiguration | O | O | O | O | O | O |
|                       | UF_MakeParameterConfiguration | O | O | O | O | O | O |
| Template Mgmt. API | UF_GetNumOfTemplate | O | O | O | O | O | O |
|                    | UF_GetMaxNumOfTemplate | O | O | O | O | O | O |
|                    | UF_GetAllUserInfo | O | O | O | O | O | O |
|                    | UF_GetAllUserInfoEx | X | X | X | X | O | O |
|                    | UF_SortUserInfo | O | O | O | O | O | O |
|                    | UF_SetUserInfoCallback | O | O | O | O | O | O |
|                    | UF_SetAdminLevel | O | O | O | O | O | O |
|                    | UF_GetAdminLevel | O | O | O | O | O | O |
|                    | UF_ClearAllAdminLevel | O | O | O | O | O | O |
|                    | UF_SaveDB | O | O | O | O | O | O |
|                    | UF_LoadDB | O | O | O | O | O | O |
|                    | UF_CheckTemplate | O | O | O | O | O | O |
|                    | UF_ReadTemplate | O | O | O | O | O | O |
|                    | UF_ReadOneTemplate | O | O | O | O | O | O |
|                    | UF_SetScanCallback | O | O | O | O | O | O |
|                    | UF_ScanTemplate | O | O | O | O | O | O |
|                    | UF_FixProvisionalTemplate | O | O | O | O |O | O |
|                    | UF_SetSecurityLevel | O | O | O | O | O | O |
|                    | UF_GetSecurityLevel | O | O | O | O | O | O |
|                    | UF_SetAuthType* | X | X | O | O | O | O |
|                    | UF_GetAuthType* | X | X | O | O | O | O |
|                    | UF_GetUserIDByAuthType* | X | X | O | O | O | O |
|                    | UF_ResetAllAuthType* | X | X | O | O | O | O |
|                    | UF_SetEntranceLimit* | X | X | O | O | O | O |
|                    | UF_GetEntranceLimit* | X | X | O | O | O | O |
|                    | UF_ClearAllEntranceLimit* | X | X | O | O | O | O |
| Image API | UF_ConvertToBitmap | O | O | O | O | O | O |
|           | UF_SaveImage | O | O | O | O | O | O |
|           | UF_LoadImage | O | O | O | O | O | O |
|           | UF_ReadImage | O | O | O | O | O | O |
|           | UF_ScanImage | O | O | O | O | O | O |
| Enroll API | UF_Enroll | O | O | O | O | O | O |
|            | UF_EnrollContinue | O | O | O | O | O | O |
|            | UF_EnrollAfterVerification | O | O | O | O | O | O |
|            | UF_EnrollTemplate | O | O | O | O | O | O |
|            | UF_EnrollMultipleTemplates | O | O | O | O | O | O |
|            | UF_EnrollImage | O | O | O | O | O | O |
|            | UF_SetEnrollCallback | O | O | O | O | O | O |
| Identify API | UF_Identify | O | O | O | O | O | O |
|              | UF_IdentifyTemplate | O | O | O | O | O | O |
|              | UF_IdentifyImage | O | O | O | O | O | O |
|              | UF_SetIdentifyCallback | O | O | O | O | O | O |
| Verify API | UF_Verify | O | O | O | O | O | O |
|            | UF_VerifyTemplate | O | O | O | O | O | O |
|            | UF_VerifyHostTemplate | O | O | O | O | O | O |
|            | UF_VerifyImage | O | O | O | O | O | O |
|            | UF_SetVerifyCallback | O | O | O | O | O | O |
| Delete API | UF_Delete | O | O | O | O | O | O |
|            | UF_DeleteOneTemplate | O | O | O | O | O | O |
|            | UF_DeleteMultipleTemplates | O | O | O | O | O | O |
|            | UF_DeleteAll | O | O | O | O | O | O |
|            | UF_DeleteByScan | O | O | O | O | O | O |
|            | UF_SetDeleteCallback | O | O | O | O | O | O |
| I/O API | UF_InitIO | X | X | O | O | O | O |
|         | UF_SetInputFunction | X | X | O | O | O | O |
|         | UF_GetInputFunction | X | X | O | O | O | O |
|         | UF_GetInputStatus | X | X | O | O | O | O |
|         | UF_GetOutputEventList | X | X | O | O | O | O |
|         | UF_ClearAllOutputEvent | X | X | O | O | O | O |
|         | UF_ClearOutputEvent | X | X | O | O | O | O |
|         | UF_SetOutputEvent | X | X | O | O | O | O |
|         | UF_GetOutputEvent | X | X | O | O | O | O |
|         | UF_SetOutputStatus | X | X | O | O | O | O |
|         | UF_SetLegacyWiegandConfig | X | X | O | O | O | O |
|         | UF_GetLegacyWiegandConfig | X | X | O | O | O | O |
|         | UF_MakeIOConfiguration | X | X | O | O | O | O |
| GPIO API | UF_GetGPIOConfiguration | O | O | X | X | X | X |
|          | UF_SetInputGPIO | O | O | X | X | X | X |
|          | UF_SetOutputGPIO | O | O | X | X | X | X |
|          | UF_SetSharedGPIO | O | O | X | X | X | X |
|          | UF_DisableGPIO | O | O | X | X | X | X |
|          | UF_ClearAllGPIO | O | O | X | X | X | X |
|          | UF_SetDefaultGPIO | O | O | X | X | X | X |
|          | UF_EnableWiegandInput | O | O | X | X | X | X |
|          | UF_EnableWiegandOutput | O | O | X | X | X | X |
|          | UF_DisableWiegandInput | O | O | X | X | X | X |
|          | UF_DisableWiegandOutput | O | O | X | X | X | X |
|          | UF_MakeGPIOConfiguration | O | O | X | X | X | X |
| User Memory API | UF_WriteUserMemory | O | O | O | O | O | O |
|                 | UF_ReadUserMemory | O | O | O | O | O | O |
| Log and Time Mgmt. API | UF_SetTime | X | X | O | O | O | O |
|                        | UF_GetTime | X | X | O | O | O | O |
|                        | UF_GetNumOfLog | X | X | O | O | O | O |
|                        | UF_ReadLog | X | X | O | O | O | O |
|                        | UF_ReadLatestLog | X | X | O | O | O | O |
|                        | UF_DeleteOldestLog | X | X | O | O | O | O |
|                        | UF_DeleteAllLog | X | X | O | O | O | O |
|                        | UF_ClearLogCache | X | X | O | O | O | O |
|                        | UF_ReadLogCache | X | X | O | O | O | O |
|                        | UF_SetCustomLogField | X | X | O | O | O | O |
|                        | UF_GetCustomLogField | X | X | O | O | O | O |
| Extended Wiegand API | UF_SetWiegandFormat | X | X | O | O | O | O |
|                      | UF_GetWiegandFormat | X | X | O | O | O | O |
|                      | UF_SetWiegandIO | X | X | O | O | O | O |
|                      | UF_GetWiegandIO | X | X | O | O | O | O |
|                      | UF_SetWiegandOption | X | X | O | O | O | O |
|                      | UF_GetWiegandOption | X | X | O | O | O | O |
|                      | UF_SetAltValue | X | X | O | O | O | O |
|                      | UF_ClearAltValue | X | X | O | O | O | O |
|                      | UF_GetAltValue | X | X | O | O | O | O |
|                      | UF_MakeWiegandConfiguration | X | X | O | O | O | O  |
| Wiegand Command Card API | UF_AddWiegandCommandCard | X | X | O | O | O | O |
|                          | UF_GetWiegandCommandCardList | X | X | O | O | O | O |
|                          | UF_ClearAllWiegandCommandCard | X | X | O | O | O | O |
| SmartCard API | UF_ReadSmartCard | X | X | X | X | X | O |
|               | UF_ReadSmartCardWithAG | X | X | X | X | X | O |
|               | UF_WriteSmartCard | X | X | X | X | X | O |
|               | UF_WriteSmartCardWithAG | X | X | X | X | X | O |
|               | UF_WriteSmartCardWithEntranceLimit* | X | X | X | X | X | O |
|               | UF_FormatSmartCard | X | X | X | X | X | O |
|               | UF_SetSmartCardMode | X | X | X | X | X | O |
|               | UF_GetSmartCardMode | X | X | X | X | X | O |
|               | UF_ChangePrimaryKey | X | X | X | X | X | O |
|               | UF_ChangeSecondaryKey | X | X | X | X | X | O |
|               | UF_SetKeyOption | X | X | X | X | X | O |
|               | UF_GetKeyOption | X | X | X | X | X | O |
|               | UF_SetCardLayout | X | X | X | X | X | O |
|               | UF_GetCardLayout | X | X | X | X | X | O |
|               | UF_SetSmartCardCallback | X | X | X | X | X | O |
| Access Control API | UF_AddTimeSchedule | X | X | X | X | O | O |
|                    | UF_GetTimeSchedule | X | X | X | X | O | O |
|                    | UF_DeleteTimeSchedule | X | X | X | X | O | O |
|                    | UF_DeleteAllTimeSchedule | X | X | X | X | O | O |
|                    | UF_AddHoliday | X | X | X | X | O | O |
|                    | UF_GetHoliday | X | X | X | X | O | O |
|                    | UF_DeleteHoliday | X | X | X | X | O | O |
|                    | UF_DeleteAllHoliday | X | X | X | X | O | O |
|                    | UF_AddAccessGroup | X | X | X | X | O | O |
|                    | UF_GetAccessGroup | X | X | X | X | O | O |
|                    | UF_DeleteAccessGroup | X | X | X | X | O | O |
|                    | UF_DeleteAllAccessGroup | X | X | X | X | O | O |
|                    | UF_SetUserAccessGroup | X | X | X | X | O | O |
|                    | UF_GetUserAccessGroup | X | X | X | X | O | O |
| Blacklist API | UF_AddBlacklist | X | X | O | O | O | O |
|               | UF_DeleteBlacklist | X | X | O | O | O | O |
|               | UF_GetBlacklist | X | X | O | O | O | O |
|               | UF_DeleteAllBlacklist | X | X | O | O | O | O |
| WSQ API | UF_ScanImageEx | X | X | X | O | X | X |
|         | UF_ReadImageEx | X | X | X | O | X | X |
|         | UF_WSQ_Decode | X | X | X | O | X | X |