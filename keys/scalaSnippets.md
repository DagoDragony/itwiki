scalaSnippets

# enumeration
```
// extends part is only for List(Status.Ok, Status.Nok) infering type Status, not Product with Serializable
sealed trait Status extends Product with Serializable

object Status {
	case object Ok extends Status
	case object Nok extends Status
}
```


