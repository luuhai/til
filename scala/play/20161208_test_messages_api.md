### Test MessagesApi

When you want to test a controller that as an injected `MessagesApi` (i.e. test form validation), build your mock controller using `GuiceApplicationBuilder` instead of `GuiceInjectorBuilder`. `GuiceApplicationBuilder` provides a default `MessagesApi`, so no need to mock one.

```scala

// Controller

class IssueController @Inject() (issueRepo: IssueRepository, val messagesApi: MessagesApi) extends Controller with I18nSupport

// Spec

val controller = new GuiceApplicationBuilder()
  .overrides(bind(classOf[IssueRepository]).toInstance(mockIssueRepository))
  .build()
  .injector
  .instanceOf[IssueController]

```
