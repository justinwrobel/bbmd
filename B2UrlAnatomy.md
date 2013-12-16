# Blackboard Block Url Anatomy

    http(s)://<blackboard-server>/webapps/<vendorId>-<handle>-<schema>/

The above is the constructed Url and the different parts are defined as follows:

    <blackboard-server> - Address of the blackboard server.
    <vendorId> - vendorId is specified in the bb-manifest.xml of the Block.
    <handle> - handle is specified in the bb-manifest.xml of the Block.
    <schema> - schema is speicifed on installation of the server. (e.g., BBLEARN, bb_bb60, etc)

## Sources/inspiration

 * [Stephen Vickers Reply to "Deep Linking To A Building Block"](http://forums.edugarage.com/forums/p/2917/8635.aspx#8635)
