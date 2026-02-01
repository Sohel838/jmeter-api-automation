```groovy

// Fetch DB value and validate

def expectedValuesList = [
    [
        "direction_1": "OUT",
        "tran_type_1": "49",
        "bene_ifsc_1": "NPCI0000001",
        "bene_account_1": "1234567991",
        "instituion_id_1": "423",
        "mcc_1":"4829",
        "response_code_1":"0000",
        "status_1": "N",
        "initiation_mode_1": "00",
        "irc_1": "0000",
        "rc_1": "0000"
        
    ]
    
    
]


def rowIndex = (Integer.parseInt(vars.get("sno") ?: "1") - 1)


if (rowIndex >= expectedValuesList.size()) {
    log.error("Row index out of bounds: ${rowIndex + 1}. No assertions executed.")
    vars.put("assertionFailureMessage", "Expected values not found: ${rowIndex + 1}.")
    AssertionResult.setFailure(true)
    AssertionResult.setFailureMessage(vars.get("assertionFailureMessage"))
    return
}


def expectedValues = expectedValuesList[rowIndex]

// Initialize failure tracking
boolean assertionFailed = false
def assertionFailMsg = []


expectedValues.each { variable, expectedValue ->
    def actualValue = vars.get(variable)?.trim()
    expectedValue = expectedValue?.trim()

    if (!(actualValue == expectedValue || (actualValue == null && expectedValue == null))) {
        assertionFailed = true
        def message = "Row ${rowIndex + 1} - Mismatch for ${variable}: Expected '${expectedValue}', got '${actualValue}'"
        assertionFailMsg << message
        log.error(message)
    }
}


vars.put("assertionFailureMessage", assertionFailMsg.join("\n"))


if (assertionFailed) {
    AssertionResult.setFailure(true)
    AssertionResult.setFailureMessage(vars.get("assertionFailureMessage"))
} else {
    AssertionResult.setFailure(false)
}
