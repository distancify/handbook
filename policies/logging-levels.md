[Handbook](../README.md) / Policies

# Logging Levels

## Error

Some unexpected error happened that needs attention. Maybe we hit an edge case that wasn’t properly handled, or maybe the database or any other external services crashed. Handled errors, such as expected exceptions, should if needed, be put as a *WARNING* or *DEBUG*.

## Warning

Used for errors that are handled and may not need direct attention, but may cause side effects that we need to be aware of. Maybe the database is down, but we handle this and put the system in “offline mode”. This state may affect other parts of the system down the line, but for now, the system will not crash. Regard this message as a “proceed with caution” statement.

Use this for monitoring important business transactions i.e an order was placed, a customer address updated etc.

## Debug

Could be anything that doesn’t fit into the above categories but is still useful to log. Primarily used by developers to fix *ERROR* messages. It’s often useful to log data that is passed from the user or read from the database. Other useful information may be the flow of the system, so logging which component is doing what is often useful for retracing what has happened to a system up to the point of an *ERROR*.

## Debug vs Trace

Some logging frameworks provide both a *TRACE* and a *DEBUG* level. I mainly see these as the same, but could be useful for implementing different retention policies. Let’s say you keep TRACE messages for 24 hours while you keep *DEBUG* messages for 7 days. *TRACE* should be regarded as a more detailed version of *DEBUG*.