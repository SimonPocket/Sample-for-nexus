# SDK per Android per Autenticazione SPID
Con l'SDK per Android si consente agli sviluppatori di integrare con poco sforzo l'autenticazione alla propria app con il protocollo SPID.
Per approfondire ulteriormente l'argomento rimandiamo a http://spid-regole-tecniche.readthedocs.io/en/latest/
I passaggi riportati di seguito ... librerire SAML , OpenSAML etc... qual è stata usata?

Infine verrà descritto il caso di test sugli ambienti creati ad hoc

## Iniziamo
Premettiamo che sono stati messi a disposizione due domini certificati per idp e sp

## 8. Aggiunta del pulsante Accedi di Facebook
Il modo più semplice per aggiungere Facebook Login alla tua app è usare LoginButton dell'SDK. LoginButton è un elemento dell'interfaccia utente che racchiude le funzionalità disponibili in LoginManager. Cliccando sul pulsante, l'utente avvia l'accesso con le autorizzazioni impostate in LoginManager. Il pulsante segue lo stato d'accesso, mostrando il testo corretto secondo lo stato di autenticazione.
Per aggiungere il pulsante Accedi di Facebook, aggiungilo innanzitutto al file XML del layout con il nome della classe completo, com.facebook.widget.LoginButton:
```
Code Snippets
```

Successivamente, configura il pulsante nell'interfaccia utente aggiungendolo a un frammento e aggiorna l'attività per usarlo.
Puoi personalizzare le proprietà di Login button e registrare una callback nel metodo onCreateView(). Puoi personalizzare le proprietà LoginBehavior, DefaultAudience, ToolTipPopup.Style e le autorizzazioni di LoginButton. Ad esempio:
```
Code Snippets
```
Se usi LoginButton in un frammento, imposta il frammento nel pulsante come mostrato, chiamando setFragment. Successivamente, chiama CallbackManager.Factory.create per creare un sistema di gestione delle callback per gestire le risposte all'accesso.

```
Code Snippets
```
Infine, chiama callbackManager.onActivityResult per passare i risultati di accesso a LoginManager tramite callbackManager.




## Built With
* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds
