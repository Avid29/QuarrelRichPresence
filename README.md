# QuarrelRichPresence

The library is based around the Object:
 ``QuarrelAppService``.
 We recommend defining an instance of this Object in a place where you can easily access it under any sircumstance where you want to update the App Status. For example, ``App.Xaml.cs``.

You initlize it with the constructor ``new QuarrelAppService("<applicationId">);"`` The application is the clientId of an app you define at https://discordapp.com/developers/applications/. **applicationId and clientId are used interchangably!**

After defining your QuarrelAppSerivce, connect to Quarrel with the function ``.TryConnectAsync()``. Naturally, this is awaitable and will return the Connection Status of the AppService, although the status can also be checked at ``QuarrelAppService.Status``. 

If the ConnectionStatus is ``Success``, you can now set the Rich Presence via ``QuarrelAppService.SetActivty(Quarrel.RichPresence.Game game, string applicationId = null)``. The ``game`` is an object defined in the library with all the variables you need to set all the data on your app, you can also send the object as a string in JSON form. If the ApplicationId was not set earlier, the variable ``applicationId`` will now set the AppServiceConnection clientId.

Example:

```
QuarrelAppService service = new QuarrelAppService("<applicationId>");
            await service.TryConnectAsync();
            if (service.Status == Windows.ApplicationModel.AppService.AppServiceConnectionStatus.Success)
            {
                await service.SetActivity(new Game() { ApplicationId = "<applicationId>", Name = "Quarrel Teset", Type = ActivityType.Playing});
            } else
            {

            }
```
