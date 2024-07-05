Two fundamental security concepts that often get confused are authentication and authorization.

## Authentication: Verifying Identity

Authentication is the process of verifying the identity of a given user. It’s ensuring that the person logging in is actually who they say they are.

There are a couple of methods of authentication, often categorized as:

**Something you know**
Usually a password, a PIN, or an answer to a security question. It’s the most commonly used authentication method, and in most cases, the start of the authentication process.

**Something you have**
Something you possess, a smart card, an authenticator application on your smartphone, or a hardware token. This is usually a device or an interface that provides a code you input alongside your password.

**Something you are**
Also known as biometric authentication, as it involves your own biometric factors such as a fingerprint, facial recognition, retina scans, and voice recognition.

### Multi Factor authentication
An MFA is a common practice of combining two or more authentication methods to confirm the identity of a user. Most commonly applications use two factors (2FA) like your password + a One Time Password from your authenticator app, or something you know + something you have.

## Authorization: Determining Access Rights
Authorization is a process of determining if an already authenticated user has access to a given object or area of a given application.

For example, an authenticated user with an Administrator role is able to access the areas of the system, and may have eleveted permissions to add, modify, or remove users from the system.

Whereas an authenticated user with an Employee role may only have access to a limited part of the system, designated for their work.
Another example you may have encountered is the superuser (root) on your Mac. This account on your Mac has unrestricted access to the whole system, while your regular user may only have access to its own directory, and only change settings related to its own account.

To use the superuser for a given account, you would typically type `sudo` ahead of the command. This prompts you to input the root user’s password (authentication) and then the command is performed with elevated permissions (authorization), accessing and modifying what a regular user may not be able to.

## Conclusion

Authentication is the act of verifying who you are, and authorization is the act of verifying what you can do or access, and authentication always precedes an authorization check.