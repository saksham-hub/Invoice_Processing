\## 🏗️ Solution Architecture



The solution follows a layered enterprise architecture:



1\. Email ingestion layer to download invoice attachments

2\. REFramework-based processing layer for transactional handling

3\. Document Understanding pipeline for OCR, classification, and extraction

4\. Validation and business rules layer

5\. Orchestrator Queue integration for scalable downstream processing





Architecture Diagram





&nbsp;                                       +--------------------------+

&nbsp;                                       |      Gmail / Outlook     |

&nbsp;                                       |     (Invoices as PDFs)   |

&nbsp;                                       +------------+-------------+

&nbsp;                                                    |

&nbsp;                                                    |

&nbsp;                                                    v

&nbsp;                                       +--------------------------+

&nbsp;                                       |      Email Downloader    |

&nbsp;                                       |     (Save Attachments)   |

&nbsp;                                       +------------+-------------+

&nbsp;                                                    |

&nbsp;                                                    |

&nbsp;                                                    |

&nbsp;                                                    |

&nbsp;                                                PDF Files

&nbsp;                                                    |

&nbsp;                                                    |

&nbsp;                                                    v

&nbsp;                                       +--------------------------+

&nbsp;                                       |                          |

&nbsp;                                       |     REFramework Bot      |

&nbsp;                                       |                          |

&nbsp;                                       +------------+-------------+

&nbsp;                                                    |

&nbsp;                                                    |

&nbsp;                   ---------------------------------------------------------------------------

&nbsp;                   |                                |                                        |

&nbsp;                   v                                v                                        v

&nbsp;           +----------------+                +----------------+                  +----------------------+

&nbsp;           |  Digitize Doc  |                |  Classify Doc  |                  |   Data Extraction    |

&nbsp;           |  (OCR + DOM)   |                | (Invoice Type) |                  |  (Invoice Fields)    |

&nbsp;           +----------------+                +----------------+                  +----------------------+

&nbsp;                                                    | 

&nbsp;                                                    |

&nbsp;                                                    | 

&nbsp;                                                    v

&nbsp;                                       +--------------------------+

&nbsp;                                       |   UiPath Orchestrator    |

&nbsp;                                       |   Queue (SpecificContent)|

&nbsp;                                       +------------+-------------+

