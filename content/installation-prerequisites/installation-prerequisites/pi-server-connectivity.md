---
uid: BIF_PIServerConnectivity
---

# PI server connectivity

<!-- Static topic. No modifications usually required -->

If a connection is lost during processing, the interface suspends all actions until it reconnects to the PI Data server or the data source. If the data source connection is down, the interface tries to reconnect on every scan until it succeeds. If the PI Data server connection is lost, the interface attempts to reconnect periodically until it times out.<!-- TU: Wondering what is meant by PI Data server -->

You can configure both the retry interval and the timeout period on the **Time Settings** tab of PI Event Frames Interface Manager. The interface logs any connection errors that occur.

**Note:** Sending tag values to multiple servers requires configuring PI Buffering on the interface node. To configure the buffering services, refer to the [Buffering section](https://docs.aveva.com/bundle/pi-server-buf-ha/page/1032385.html) of the AVEVA PI Server - Buffering and High Availability guide. 

Additionaly, creating tags and other configuration updates to multiple servers requires all servers to be part of a PI Server Collective. For additional information on how to configure collectives, refer to [PI Data Archive collective management](https://docs.osisoft.com/bundle/pi-server/page/pi-data-archive-collective-management.html) in the AVEVA PI Server guide.
