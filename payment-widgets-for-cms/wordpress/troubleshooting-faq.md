# Troubleshooting (FAQ)

## Troubleshooting (FAQ)

#### The token "flies off" (disappears/resets) after saving settings

Ensure that the page option is added to the list of allowed parameters (settings API) and that the user has administrator rights.

#### Incorrect time in "Token valid until"

Check the website's time zone. You can output the `tokenExpiration` from the bank's gateway logs and compare it with the actual time.

#### Re-authorization

According to the bank's terms, the token is valid for 24 hours; automatic renewal is performed approximately every 12 hours. The _Re-authorize Now_ button updates the token manually.

#### Console errors (404) for log files

If there are no logs yet, the plugin does not show an error on the page, but there may be a 404 error in DevTools for the request. This is not critical; the file will appear after the first successful write.

#### Payment method not displayed on checkout

The checkout page must necessarily contain the shortcode `[woocommerce_checkout]`.
