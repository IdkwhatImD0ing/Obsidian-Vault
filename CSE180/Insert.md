 - If a new row is inserted and a value is specified for an attribute, the attribute receives the value
 - If there is no attribute supplied and there is a DEFAULT value, then the attribute will be the default
 - If there is no value and no DEFAULT, and the value is allowed to be NULL, the value will be NULL
 - Else, an error will be thrown


