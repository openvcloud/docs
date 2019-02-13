# Consumption API
# Used to retrieve consumption data for an account or for the whole environment

## endpoint: GET /restmachine/cloudapi/billing/calculate
## parameters:

### start: Epoch of the time that will be used to collect the consumption data from
### end: Epoch of the time that will be used to collect the consumption data to
### accountId: [Optional] Only output records for account with accountId

# Result definition

When accountid is specified, the return a detailed overview of the capacity unit consumption.
```
{
   "account": {
          "id": 1,
          "name": "NASA",
          "cloudspaces": {
              "1": {
                  "id": 1,
                  "name": "Houston flight control",
                  "machines": {
                      "1": {
                          "id": 1,
                          "name": "Endavor"
                          "consumption": {
                              "CU": 1.202324,
                              "SU": 2.123456,
                              "TU": 0.509384
                      },
                      "2": {
                          "id": 1,
                          "name": "Discovery"
                          "consumption": {
                              "CU": 1.090876,
                              "SU": 2.4123456,
                              "TU": 0.800982
                      }
                  },
                  "consumption": {
                      "CU": 2.000287,
                      "SU": 4.509876,
                      "TU": 1.390897,
                      "NU": 0.459087
                  }
              }
          },
          "consumption": {
              "CU": 2.009876,
              "SU": 4.534765,
              "TU": 1.312098,
              "NU": 0.450098
          }
  }
}

```
Without accountid, only return the total G8 consumption
```
{
    "consumption": {
      "CU": 2.009876,
      "SU": 4.500987,
      "TU": 1.300098,
      "NU": 0.451209
   }

}
```
# Authentication
To be able to access the API the user account must have access to the billing group.