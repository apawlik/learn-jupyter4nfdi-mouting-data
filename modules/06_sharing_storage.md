# Sharing data from mounted storage

Jupyter4NFDI allows mounted storage to be shared with others without giving another person your storage password or access key.

The important idea is separation of **access** from **credentials**. The collaborator gets access to the mounted data through the shared environment. They do not need your storage password which would be giving them your credentials.

If people only need to inspect a dataset, a read-only mount is usually safer than a read-write mount. A shared read-write mount can allow other users to create, change or delete files, depending on the permissions of the underlying storage.

For example, if you are teaching a workshop. Everyone needs access to training-data but nobody should change the source files.
A read-only mount makes sense.

Now imagine a research team jointly producing files under: project-results. Read-write access may be appropriate, but everybody should understand that they are modifying shared storage.

Avoid  sending somebody your credentials such as your username and password or placing secrets in a shared notebook.
Use the access and sharing mechanisms provided by the platform instead.

