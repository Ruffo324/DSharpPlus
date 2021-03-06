Reference for ``DiscordClient``
===============================

``DiscordClient`` is the heart of the library and your bot. It's the class that takes care of dispatching events, 
communicating on your bot's behalf, and performing other tasks.

Constructors
------------

.. function:: DiscordClient()

	.. note::
	
		It is generally a better idea to use the constructor which allows you to specify a configuration.

	Initializes the client with default configuration.

.. function:: DiscordClient(config)

	Initializes the client with specified configuration.
	
	:param config: An instance of :doc:`DiscordConfig </reference/misc/DiscordConfig>`. Used to specify the configuration options for the client.

Events
------

.. attribute:: SocketOpened

	Called when the WebSocket connection is established. Takes no arguments.

.. attribute:: SocketClosed

	Called when the WebSocket connection is closed. Takes no arguments.

.. attribute:: Ready

	Called when the client enters ready state. Takes no arguments.

.. attribute:: ChannelCreated

	Called when a new channel is created. Takes ``ChannelCreateEventArgs`` as an argument, with following parameters:
	
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) that was just created.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) that the channel was created in.

.. function DMChannelCreated

	Called when a new DM channel is created. Takes ``DMChannelCreateEventArgs`` as an argument, with following 
	parameters:
	
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) that was just created.

.. attribute:: ChannelUpdated

	Called when an existing channel is updated. Takes ``ChannelUpdateEventArgs`` as an argument, with following 
	parameters:
	
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) that was just updated.
	:param ChannelBefore: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) before it was updated.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) that the channel was updated in.

.. attribute:: ChannelDeleted

	Called when an existing channel is deleted. Takes ``ChannelDeleteEventArgs`` as an argument, with following 
	parameters:
	
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) that was just deleted.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) that the channel was deleted in.

.. attribute:: DMChannelDeleted

	Called when an existing DM channel is deleted. Takes ``DMChannelDeleteEventArgs`` as an argument, with following 
	parameters:
	
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) that was just deleted.

.. attribute:: GuildCreated

	Called when a new guild is created. Takes ``GuildCreateEventArgs`` as an argument, with following parameters:
	
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) that was just created.

.. attribute:: GuildAvailable

	Called when a guild becomes available. Takes ``GuildCreateEventArgs`` as an argument, with following parameters:
	
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) that has just become available.

.. attribute:: GuildUpdated

	Called when a guild is updated. Takes ``GuildUpdateEventArgs`` as an argument, with following parameters:
	
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) that was just updated.

.. attribute:: GuildDeleted

	Called when a guild is deleted. Takes ``GuildDeleteEventArgs`` as an argument, with following parameters:
	
	:param ID: ID of the guild that was just deleted.
	:param Unavailable: Whether the guild is unavailable or not.

.. attribute:: GuildUnavailable

	Called when a guild becomes unavailable. Takes ``GuildDeleteEventArgs`` as an argument, with following parameters:
	
	:param ID: ID of the guild that has just become unavailable.
	:param Unavailable: Whether the guild is unavailable or not.

.. attribute:: MessageCreated

	Called when the client receives a new message. Takes ``MessageCreateEventArgs`` as an argument, with following 
	parameters:
	
	:param Message: The message (instance of :doc:`DiscordMessage </reference/DiscordMessage>`) that was received.
	:param MentionedUsers: A list of :doc:`DiscordMember </reference/DiscordMember>` that were mentioned in this message.
	:param MentionedRoles: A list of :doc:`DiscordRole </reference/DiscordRole>` that were mentioned in this message.
	:param MentionedChannels: A list of :doc:`DiscordChannel </reference/DiscordChannel>` that were mentioned in this message.
	:param UsedEmojis: A list of :doc:`DiscordEmoji </reference/entities/DiscordEmoji>` that were used in this message.
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) the message was sent in.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) the message was sent in. This parameter is ``null`` for direct messages.
	:param Author: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) that sent the message.

.. attribute:: PresenceUpdate

	Called when a presence update occurs. Takes ``PresenceUpdateEventArgs`` as an argument, with following parameters:
	
	:param User: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) whose presence was updated.
	:param UserID: The ID of the user whose presence was updated.
	:param Game: Game the user is playing or streaming.
	:param Status: User's status (online, idle, do not disturb, or offline).
	:param GuildID: ID of the guild the presence update occured in.
	:param RoleIDs: IDs of user's roles in the given guild.
	:param PresenceBefore: User's presence before it was updated.

.. attribute:: GuildBanAdd

	Called whenever a user gets banned from a guild. Takes ``GuildBanAddEventArgs`` as an argument, with following 
	parameters:
	
	:param User: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) that got banned.
	:param GuildID: ID of the guild the user got banned from.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) that the user got banned from.

.. attribute:: GuildBanRemove

	Called whenever a user gets unbanned from a guild. Takes ``GuildBanRemoveEventArgs`` as an argument, with 
	following parameters:
	
	:param User: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) that got unbanned.
	:param GuildID: ID of the guild the user got unbanned from.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) that the user got unbanned from.

.. attribute:: GuildEmojisUpdate

	Called whenever a guild has its emoji updated. Takes ``GuildEmojisUpdateEventArgs`` as an argument, with the 
	following parameters:
	
	:param Emojis: A list of :doc:`DiscordEmoji </reference/entities/DiscordEmoji>` that got updated.
	:param EmojisBefore: A list of :doc:`DiscordEmoji </reference/entities/DiscordEmoji>` before they got updated.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) that had its emoji updated.

.. attribute:: GuildIntegrationsUpdate

	Called whenever a guild has its integrations updated. Takes ``GuildIntegrationsUpdateEventArgs`` as an argument, 
	with following parameters:
	
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) that had its integrations updated.

.. attribute:: GuildMemberAdd

	Called whenever a member joins a guild. Takes ``GuildMemberAddEventArgs`` as an argument, with following 
	parameters:
	
	:param Member: The member (instance of :doc:`DiscordMember </reference/DiscordMember>`)
	:param GuildID: ID of the guild the memeber joined.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) the member joined.

.. attribute:: GuildMemberRemove

	Called whenever a member leaves a guild. Takes ``GuildMemberRemoveEventArgs`` as an argument, with following 
	parameters:
	
	:param GuildID: ID of the guild that the member left.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) the member left.
	:param User: The member (instance of :doc:`DiscordUser </reference/DiscordUser>`) that left the guild.

.. attribute:: GuildMemberUpdate

	Called whenever a guild member is updated. Takes ``GuildMemberUpdateEventArgs`` as an argument, with following 
	parameters:
	
	:param GuildID: ID of the guild in which the update occured.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) in which the update occured.
	:param Roles: A list of role IDs for the member.
	:param RolesBefore: A list of old role IDs for the member.
	:param NickName: New nickname of the member.
	:param NickNameBefore: Old nickname of the member.
	:param User: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) that got updated.

.. attribute:: GuildRoleCreate

	Called whenever a role is created in a guild. Takes ``GuildRoleCreateEventArgs`` as an argument, with following 
	parameters:
	
	:param GuildID: ID of the guild the role was created in.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) the role was created in.
	:param Role: The role (instance of :doc:`DiscordRole </reference/DiscordRole>`) that was created.

.. attribute:: GuildRoleUpdate

	Called whenever a role is updated in a guild. Takes ``GuildRoleUpdateEventArgs`` as an argument, with following 
	parameters:
	
	:param GuildID: ID of the guild the role was updated in.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) the role was updated in.
	:param Role: The role (instance of :doc:`DiscordRole </reference/DiscordRole>`) that was updated.
	:param RoleBefore: The role (instance of :doc:`DiscordRole </reference/DiscordRole>`) before it was updated.

.. attribute:: GuildRoleDelete

	Called whenever a role is deleted in a guild. Takes ``GuildRoleDeleteEventArgs`` as an argument, with following 
	parameters:
	
	:param GuildID: ID of the guild the role was deleted in.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) the role was deleted in.
	:param Role: The role (instance of :doc:`DiscordRole </reference/DiscordRole>`) that was deleted.

.. attribute:: MessageUpdate

	Called whenever a message is updated. Takes ``MessageUpdateEventArgs`` as an argument, with following parameters:
	
	:param Message: The message (instance of :doc:`DiscordMessage </reference/DiscordMessage>`) that was updated.
	:param MentionedUsers: A list of :doc:`DiscordMember </reference/DiscordMember>` that were mentioned in this message.
	:param MentionedRoles: A list of :doc:`DiscordRole </reference/DiscordRole>` that were mentioned in this message.
	:param MentionedChannels: A list of :doc:`DiscordChannel </reference/DiscordChannel>` that were mentioned in this message.
	:param UsedEmojis: A list of :doc:`DiscordEmoji </reference/entities/DiscordEmoji>` that were used in this message.
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) the message was updated in.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) the message was updated in. This parameter is ``null`` for direct messages.
	:param Author: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) that updated the message.

.. attribute:: MessageDelete

	Called whenever a message is deleted. Takes ``MessageDeleteEventArgs`` as an argument, with following parameters:
	
	:param MessageID: ID of the message that was deleted.
	:param ChannelID: ID of the channel the message was deleted in.
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) the message was deleted in.

.. attribute:: MessageBulkDelete

	Called whenever several messages are deleted at once. Takes ``MessageBulkDeleteEventArgs`` as an argument, with 
	following parameters:
	
	:param MessageIDs: A list of IDs of messages that were deleted.
	:param ChannelID: ID of the channel the messages were deleted in.
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) the messages were deleted in.

.. attribute:: TypingStart

	Called whenever a user starts typing in a channel. Takes ``TypingStartEventArgs`` as an argument, with following 
	parameters:
	
	:param ChannelID: ID of the channel the user started typing in.
	:param UserID: ID of the user that started typing.
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) the user started typing in.
	:param User: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) that started typing.

.. attribute:: UserSettingsUpdate

	Called whenever user's settings are updated. Takes ``UserSettingsUpdateEventArgs`` as an argument, with following 
	parameters:
	
	:param User: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) whose settings were updated.
	
.. attribute:: UserUpdate

	Called whenever a user is updated. Takes ``UserUpdateEventArgs`` as an argument, with following parameters:
	
	:param User: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) that was updated.
	:param UserBefore: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) before it was updated.

.. attribute:: VoiceStateUpdate

	Called whenever a user's voice state is updated. Takes ``VoiceStateUpdateEventArgs`` as an argument, with 
	following parameters:
	
	:param UserID: ID of the user whose voice state was updated.
	:param GuildID: ID of the guild where the voice state update occured.
	:param User: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) whose voice state was updated.
	:param SessionID: ID of the voice session for the user.

.. attribute:: VoiceServerUpdate

	.. note::
	
		This event is used when negotiating voice information with Discord. It shouldn't be used by bots.

	Called whenever voice connection data is sent to the client. Takes ``VoiceServerUpdateEventArgs`` as an argument, 
	with following parameters:
	
	:param VoiceToken: Token for the voice session.
	:param GuildID: ID of the guild the client is connecting to.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) the client is connecting to.
	:param Endpoint: Voice endpoint to connect to.

.. attribute:: GuildMembersChunk

	.. note::
	
		This event is used when connecting to discord and requesting more members. It shouldn't be used by bots.
	
	Called whenever another batch of guild members is sent to client. Takes ``GuildMembersChunkEventArgs`` as an 
	argument, with following parameters:
	
	:param GuildID: ID of the guild for which the members were received.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) for which the members were received.
	:param Members: A list of :doc:`DiscordMember </reference/DiscordMember>` received in this chunk.

.. attribute:: UnknownEvent

	.. warning::
	
		This event indicates something went terribly wrong. If you ever see this event, please report it on the 
		`issue tracker <https://github.com/NaamloosDT/DSharpPlus/issues>`_ with details.
	
	Called whenever an unknown event is dispatched to the client. Takes ``UnknownEventArgs`` as an argument, with 
	following parameters:
	
	:param EventName: Event's name.
	:param Json: Event's payload.

.. attribute:: MessageReactionAdd

	Called whenever a message has a reaction added to it. Takes ``MessageReactionAddEventArgs`` as an argument, with 
	following parameters:
	
	:param UserID: ID of the user who added the reaction.
	:param MessageID: ID of the message the reaction was added to.
	:param ChannelID: ID of the channel the message is located in.
	:param Emoji: The emoji (instance of :doc:`DiscordEmoji </reference/DiscordEmoji>`) that was used to react to the message.
	:param User: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) who reacted to the message.
	:param Message: The message (instance of :doc:`DiscordMessage </reference/DiscordMessage>`) the reaction was added to.
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) the message is located in.

.. attribute:: MessageReactionRemove

	Called whenever a message has a reaction removed from it. Takes ``MessageReactionRemoveEventArgs`` as an argument, 
	with following parameters:
	
	:param UserID: ID of the user who removed the reaction.
	:param MessageID: ID of the message the reaction was removed from.
	:param ChannelID: ID of the channel the message is located in.
	:param Emoji: The emoji (instance of :doc:`DiscordEmoji </reference/DiscordEmoji>`) that was used to react to the message.
	:param User: The user (instance of :doc:`DiscordUser </reference/DiscordUser>`) who removed the reaction.
	:param Message: The message (instance of :doc:`DiscordMessage </reference/DiscordMessage>`) the reaction was removed from.
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) the message is located in.

.. attribute:: MessageReactionRemoveAll

	Called whenever a message has all of its reactions remvoed from it. Takes ``MessageReactionRemoveAllEventArgs`` as 
	an argument, with following parameters:
	
	:param MessageID: ID of the message the reactions were removed from.
	:param ChannelID: ID of the channel the message is located in.
	:param Message: The message (instance of :doc:`DiscordMessage </reference/DiscordMessage>`) the reactions were removed from.
	:param Channel: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) the message is located in.

.. attribute:: WebhooksUpdate

	Called whenever webhooks are updated. Takes ``WebhooksUpdateEventArgs`` as an argument, with following parameters:
	
	:param GuildID: ID of the guild the webhook was updated in.
	:param Guild: The guild (instance of :doc:`DiscordGuild </reference/DiscordGuild>`) the webhook was updated in.
	:param ChannelID: ID of the channel the webhook was updated in.
	:param Channe: The channel (instance of :doc:`DiscordChannel </reference/DiscordChannel>`) the webhook was updated in.

Members
-------

.. attribute:: DebugLogger

	An instance of :doc:`DebugLogger </reference/misc/DebugLogger>` used to log messages from the library.

.. attribute:: GatewayVersion

	Version of the gateway used by the library.

.. attribute:: GatewayUrl

	URL of the gateway used by the library.

.. attribute:: Shards

	Recommended shard count for this bot.

.. attribute:: Me

	The user the bot is connected as (instance of :doc:`DiscordUser </reference/DiscordUser>`).

.. attribute:: PrivateChannels

	List of DM channels (instances of :doc:`DiscordDMChannel </reference/DiscordDMChannel>`).
	
.. attribute:: Guilds

	A dictionary of guilds (instances of :doc:`DiscordGuild </reference/DiscordGuild>`) the bot is in.

Methods
-------

.. function:: Connect()
.. function:: Connect(tokenOverride, tokenType)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	.. note::
	
		If you did not specify a token or config when constructing the client, you will need to use the overload with 
		token overrides.
	
	Connects to Discord and begins dispatching events.
	
	:param tokenOverride: A string containing the token used to connect.
	:param tokenType: A :doc:`TokenType </reference/misc/TokenType>` which defines the token's type.
	
.. function:: AddModule(module)

	Adds a module to the client, and returns it.
	
	:param module: An instance of a class implementing :doc:`IModule </reference/misc/IModule>` interface.
	
.. function:: GetModule<T>(module)

	Finds and returns an instance of the module specified by the generic argument. ``T`` needs to be a class 
	implementing :doc:`IModule </reference/misc/IModule>` interface.

.. function:: Reconnect()
.. function:: Reconnect(tokenOverride, tokenType, shard)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	.. note::
	
		If you did not specify a token or config when constructing the client, you will need to use the overload with 
		token overrides.

	Reconnects with Discord.
	
	:param tokenOverride: A string containing the token used to connect.
	:param tokenType: A :doc:`TokenType </reference/misc/TokenType>` which defines the token's type.
	:param shard: Shard to connect.

.. function:: Disconnect()

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Disconnects from Discord and stops dispatching events.
	
.. function:: GetUser(user)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Gets a user by name.
	
	:param name: Name of the user.

.. function:: DeleteChannel(id)
.. function:: DeleteChannel(channel)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Deletes a channel.
	
	:param id: ID of the channel to delete.
	:param channel: An instance of :doc:`DiscordChannel </reference/DiscordChannel>` to delete.

.. function:: GetMessage(channel, messageID)
.. function:: GetMessage(channelID, messageID)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Gets a specified message from the specified channel.
	
	:param channel: An instance of :doc:`DiscordChannel </reference/DiscordChannel>` to get the message from.
	:param channelID: ID of the channel to get the message from.
	:param messageID: ID of the message to get.

.. function:: GetChannel(id)
.. function:: GetChannelByID(id)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Gets a channel.
	
	:param id: ID of the channel to get.

.. function:: SendMessage(channel, contents, tts, embed)
.. function:: SendMessage(dmchannel, contents, tts, embed)
.. function:: SendMessage(channelid, contents, tts, embed)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Sends a message to specified channel.
	
	:param channel: An instance of :doc:`DiscordChannel </reference/DiscordChannel>` to send the message to.
	:param dmchannel: An instance of An instance of :doc:`DiscordDMChannel </reference/DiscordDMChannel>` to send the message to.
	:param channelid: ID of the channel to send the message to.
	:param contents: Contents of the message to send.
	:param tts: Whether the message is a TTS message or not. Optional, defaults to ``false``.
	:param embed: Embed to attach to the message. Optional, defaults to ``null``.

.. function:: CreateGuild(name)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Creates a new guild and returns it.
	
	:param name: Name of the guild to create.

.. function:: GetGuild(id)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Gets a guild by ID.
	
	:param id: ID of the guild to get.

.. function:: DeleteGuild(id)
.. function:: DeleteGuild(guild)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Deletes a guild.
	
	:param id: ID of the guild to delete.
	:param guild: An instance of :doc:`DiscordGuild </reference/DiscordGuild>` to delete.

.. function:: GetInviteByCode(code)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	.. note::
	
		This method is not usable by bot users.
	
	.. warning::
	
		Using this method on a user account will unverify your account and flag you for raiding.
	
	Gets a guild invite by code.
	
	:param code: Invite code to get the invite for.

.. function:: GetConnections()

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Gets connections for the current user.

.. function:: ListRegions()

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Gets the list of voice regions.

.. function:: GetWebhook(id)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Gets a webhook by ID.
	
	:param id: ID of the webhook to get.

.. function:: GetWebhookWithToken(id, token)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Gets a webhook with a token by ID.
	
	:param id: ID of the webhook to get.
	:param token: Webhook's token.

.. function:: CreateDM(id)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Creates a DM channel between the bot and the specified user.
	
	:param id: ID of the user to create a DM channel with.

.. function:: UpdateStatus(game, idle_since)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Updates current user's status.
	
	:param game: Game to set in the status. Optional, defaults to empty string.
	:param idle_since: How long has the user been idle. Optional, defaults to ``-1`` (not idle).

.. function:: ModifyMember(guildID, memberID, nickname, roles, muted, deaf, voiceChannelID)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Updates a member with specified parameters.
	
	:param guildID: ID of the guild to update the member in.
	:param memberID: ID of the member to update.
	:param nickname: New nickname for the member. Optional, defaults to ``null``.
	:param roles: List of role IDs to set for this user. Optional, defaults to ``null``.
	:param muted: Whether the user should be muted in voice. Optional, defaults to ``false``.
	:param deaf: Whether the user should be deafened in voice. Optional, defaults to ``false``.
	:param voiceChannelID: ID of the voice channel to put the user in. Optional, defaults to ``0`` (no channel).

.. function:: GetCurrentApp()

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Gets the current application.

.. function:: GetUserPresence(id)

	Gets presence for specified user.
	
	:param id: ID of the user to get the presence of.

.. function:: ListGuildMembers(guildID, limit, after)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Gets a page of guild members.
	
	:param guildID: ID of the guild to get the members of.
	:param limit: Maximum number of users to get. Value cannot exceed ``100``.
	:param after: ID of the user after which to get more users.

.. function:: SetAvatar(path)

	.. note:: 
	
		This method is asynchronous. It needs to be awaited.
	
	Updates the current user's avatar.
	
	:param path: Path to the file with the new avatar.

Additional notes
----------------

``DiscordClient`` has several extensions available, which extend its functionality in various ways.

Command module
^^^^^^^^^^^^^^

Several command-specific :doc:`extensions </reference/commands/DiscordClient-extensions>` are defined in that module, which enable the its usage.

VoiceNext module
^^^^^^^^^^^^^^^^

Several voice-specific :doc:`extensions </reference/voice/DiscordClient-extensions>` are defined in that module, which enable the its usage.