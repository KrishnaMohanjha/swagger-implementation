# swagger-implementation
<!-- spring openapi implementation-->

		<dependency>
			<groupId>org.springdoc</groupId>
			<artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
			<version>2.5.0</version>
		</dependency>


application.properties

#spring open-api config
springdoc-swagger-ui.path=/swagger-ui.html 
springdoc.api-docs.path=/api-docs

import io.swagger.v3.oas.annotations.Operation;
import io.swagger.v3.oas.annotations.Parameter;
import io.swagger.v3.oas.annotations.responses.ApiResponse;
import io.swagger.v3.oas.annotations.responses.ApiResponses;


	// Push App Notification
	@Operation(summary = "Push a notification to app", description = "Sends a push notification to the app.")
	@ApiResponses(value = {
			@ApiResponse(responseCode = "200", description = "Notification successfully sent",
					content = @Content(mediaType = "application/json")),
			@ApiResponse(responseCode = "400", description = "Invalid notification data",
					content = @Content(mediaType = "application/json")),
			@ApiResponse(responseCode = "500", description = "Internal server error",
					content = @Content(mediaType = "application/json"))
	})
	@PostMapping("/pushAppNotification")
	public ResponseEntity<Object> pushAppNotification(@io.swagger.v3.oas.annotations.parameters.RequestBody(
			description = "Push notification details",
			required = true,
			content = @Content(schema = @Schema(implementation = PushNotificationVo.class))
	)@RequestBody PushNotificationVo notificationVo) {
