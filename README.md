# notes-and-code-fragments
public class MongoStatusListener implements CommandListener {
 +
 +
 +    @Override
 +    public void commandStarted(CommandStartedEvent commandStartedEvent) {
 +        System.out.println(String.format("Sent command '%s:%s' with id %s to database '%s' "
 +                        + "on connection '%s' to server '%s'",
 +                commandStartedEvent.getCommandName(),
 +                commandStartedEvent.getCommand().get( commandStartedEvent.getCommandName()),
 +                commandStartedEvent.getRequestId(),
 +                commandStartedEvent.getDatabaseName(),
 +                commandStartedEvent.getConnectionDescription()
 +                        .getConnectionId(),
 +                commandStartedEvent.getConnectionDescription().getServerAddress()));
 +    }
 +
 +    @Override
 +    public void commandSucceeded(CommandSucceededEvent commandSucceededEvent) {
 +        System.out.println(String.format("Successfully executed command '%s' with id %s "
 +                        + "on connection '%s' to server '%s'",
 +                commandSucceededEvent.getCommandName(),
 +                commandSucceededEvent.getRequestId(),
 +                commandSucceededEvent.getConnectionDescription()
 +                        .getConnectionId(),
 +                commandSucceededEvent.getConnectionDescription().getServerAddress()));
 +    }
 +
 +    @Override
 +    public void commandFailed(CommandFailedEvent commandFailedEvent) {
 +        System.out.println(String.format("Failed execution of command '%s' with id %s "
 +                        + "on connection '%s' to server '%s' with exception '%s'",
 +                commandFailedEvent.getCommandName(),
 +                commandFailedEvent.getRequestId(),
 +                commandFailedEvent.getConnectionDescription()
 +                        .getConnectionId(),
 +                commandFailedEvent.getConnectionDescription().getServerAddress(),
 +                commandFailedEvent.getThrowable()));
 +    }
