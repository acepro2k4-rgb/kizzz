#!url=https://raw.githubusercontent.com/acepro2k4-rgb/kizzz/main/Locket_Gold_Auditable.sgmodule
#!name=Locket Gold - Auditable Version
#!desc=Safe & Transparent Locket Gold Unlocker | No External Dependencies | Fully Reviewable

# ============================================
# SECURITY NOTICE
# ============================================
# This module contains INLINE scripts for full transparency
# No external URLs = No data collection risks
# All code is reviewable in this single file
# ============================================

[Script]

# REVENUECAT RESPONSE HANDLER
# Purpose: Modifies RevenueCat API responses to unlock premium features
# Security: Operates only on RevenueCat domain, no external calls
revenuecat_handler = type=http-response, pattern=^https:\/\/api\.revenuecat\.com\/.+\/(receipts$|subscribers\/[^/]+$), requires-body=true, max-size=-1, timeout=60, script-path=Locket_Gold_Auditable.js

# REQUEST HEADER CLEANUP
# Purpose: Removes etag headers to prevent RevenueCat cache validation
# Security: Simple header deletion, no data exfiltration
delete_etag = type=http-request, pattern=^https:\/\/api\.revenuecat\.com\/.+\/(receipts|subscribers), timeout=60, script-path=Locket_Gold_DeleteHeader.js

[MITM]
# MINIMAL SCOPE: Only intercepts RevenueCat API calls
# No YouTube, Spotify, or SoundCloud interception
hostname = api.revenuecat.com
